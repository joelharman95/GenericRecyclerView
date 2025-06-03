# GenericRecyclerView
With View and DataBinding combined, single lined initialisation takes only model and layout

**Usage**
myAdapter = GenericRecyclerViewAdapter(mutableListOf<DataModel>(), R.layout.layout_recycler_view_item, null)


@JvmStatic
@BindingAdapter("favouritePlacesAdapter", "favouritePlaces")
fun <T, A> RecyclerView.myAdapter(myAdapter: GenericRecyclerViewAdapter<T, A>?, dataModel : List<DataModel>?) {
    if (myAdapter != null) {
        if (adapter == null) {
            adapter = myAdapter
        }
        dataModel?.let {
          myAdapter.addList(dataModel as MutableList<T>)
        } ?: myAdapter.addList(mutableListOf<FavoritesData>() as MutableList<T>)
    }
}
