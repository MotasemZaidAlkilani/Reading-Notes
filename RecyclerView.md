# Create dynamic lists with RecyclerView

##  RecyclerView
it's efficiently way to display large sets of data ,and dynamically create what u need ,after u define the data and how it's looks.

now recycleview display elements on screen , when u scroll down and element in top hide ,the recycle view will not destroy it , instead will use for new bottom element .

recycleview is viewgroup , and element defined by view object

## Steps for implementing your RecyclerView

1-decide how will look like the list 

2-design each element in list how look and how behave 

3-define adapter that will connect the data to viewholder.

## three layout managers :

1-LinearLayoutManager arranges the items in a one-dimensional list.

2-GridLayoutManager arranges all items in a two-dimensional grid

3-StaggeredGridLayoutManager is similar to GridLayoutManager ,but it does not require that items in a row have the same height
 or items in the same column have the same width .
 
 ## When you define your adapter, you need to override three key methods :
 
 1-onCreateViewHolder(): calls this method whenever it needs to create a new ViewHolder
 
 2-onBindViewHolder():calls this method to associate a ViewHolder with data
 
 3-getItemCount(): calls this method to get the size of the data set
 
 _____
 
 ```
 public class CustomAdapter extends RecyclerView.Adapter<CustomAdapter.ViewHolder> {

    private String[] localDataSet;

    /**
     * Provide a reference to the type of views that you are using
     * (custom ViewHolder).
     */
    public static class ViewHolder extends RecyclerView.ViewHolder {
        private final TextView textView;

        public ViewHolder(View view) {
            super(view);
            // Define click listener for the ViewHolder's View

            textView = (TextView) view.findViewById(R.id.textView);
        }

        public TextView getTextView() {
            return textView;
        }
    }

    /**
     * Initialize the dataset of the Adapter.
     *
     * @param dataSet String[] containing the data to populate views to be used
     * by RecyclerView.
     */
    public CustomAdapter(String[] dataSet) {
        localDataSet = dataSet;
    }

    // Create new views (invoked by the layout manager)
    @Override
    public ViewHolder onCreateViewHolder(ViewGroup viewGroup, int viewType) {
        // Create a new view, which defines the UI of the list item
        View view = LayoutInflater.from(viewGroup.getContext())
                .inflate(R.layout.text_row_item, viewGroup, false);

        return new ViewHolder(view);
    }

    // Replace the contents of a view (invoked by the layout manager)
    @Override
    public void onBindViewHolder(ViewHolder viewHolder, final int position) {

        // Get element from your dataset at this position and replace the
        // contents of the view with that element
        viewHolder.getTextView().setText(localDataSet[position]);
    }

    // Return the size of your dataset (invoked by the layout manager)
    @Override
    public int getItemCount() {
        return localDataSet.length;
    }
}
```
