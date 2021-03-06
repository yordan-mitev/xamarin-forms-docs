---
title: ListView Load On Demand
page_title: ListView Load On Demand
slug: ios-listview-load-on-demand
position: 11
---

# ListView for Xamarin.iOS: Load-on-demand

There are certain scenarios typically with remote data over the wire where data needs to be loaded continuously on small portions. TKListView can load data on demand.

## Enabling the load-on-demand

To enable the load on demand feature, you shoud set the <code>LoadOnDemandMode</code> property to one of the two supported modes <code>Auto</code> or <code>Manual</code>.

```C#
listView.LoadOnDemandMode = TKListViewLoadOnDemandMode.Manual;
```

When using the `Auto` LoadOnDemand mode the <code>LoadOnDemandBufferSize</code> of type `int` property defines the number of cells from the bottom of the list view up at which to start requesting data. 

```C#
listView.LoadOnDemandBufferSize = 5;
```

After setting the desired <code>LoadOnDemandMode</code> you should implement the <code>TKListViewDelgate</code> method <code>ShouldLoadMoreDataAtIndexPath:</code> to determine if more data should be loaded. After the data is loaded you should notify the ListView by calling its <code>DidLoadDataOnDemand</code> method:

```C#
class ListViewDelegate: TKListViewDelegate
{
    ListViewLoadOnDemand owner;

    public ListViewDelegate(ListViewLoadOnDemand owner)
    {
        this.owner = owner;
    }

    public override bool ShouldLoadMoreDataAtIndexPath (TKListView listView, NSIndexPath indexPath)
    {
        DispatchQueue.DefaultGlobalQueue.DispatchAsync (() => {
            this.owner.lastRetrievedDataIndex = Math.Min(this.owner.names.Items.Length, this.owner.lastRetrievedDataIndex + 10);
            DispatchQueue.MainQueue.DispatchAfter(new DispatchTime(DispatchTime.Now, 2 * 400000000), new Action(delegate {
                if (this.owner.names.Items.Length == this.owner.lastRetrievedDataIndex) {
                    listView.LoadOnDemandMode = TKListViewLoadOnDemandMode.None;
                }
                listView.DidLoadDataOnDemand();                
            }));
        });

        return true;
    }
}
```

When using `Manual` LoadOnDemand mode, TKListView appends a special cell at the end of the list. Touching this cell starts the process of loading more data. In this scenario you should process `CellForItem` method of TKListViewDataSource and check whether this is a "load on demand cell":

```C#
public override TKListViewCell CellForItem (TKListView listView, NSIndexPath indexPath)
{
    TKListViewCell cell = listView.DequeueLoadOnDemandCell (indexPath);

    if (cell == null) {
        cell = listView.DequeueReusableCell ("cell", indexPath) as TKListViewCell;
        cell.ImageView.Image = UIImage.FromBundle (this.owner.photos.Items [indexPath.Row] as NSString);
        cell.TextLabel.Text = this.owner.names.Items [indexPath.Row] as NSString;
        Random r = new Random ();
        cell.DetailTextLabel.Text = this.owner.loremIpsum.RandomString (10 + r.Next (0, 16), indexPath);
        cell.DetailTextLabel.TextColor = UIColor.White;
    }

    cell.BackgroundView.BackgroundColor = UIColor.FromWhiteAlpha (0.3f, 0.5f);
    ((TKView)cell.BackgroundView).Stroke = null;

    return cell;
}
```

> ListView Load On Demand example can be found in our [Native Xamarin.iOS examples]({%slug developer-focused-examples%}#native-only-examples).