---
layout: post
title: AndroidSupport 使用过程中遇到的问题
---

 1.android.support.v7.widget.AppCompatxxxx  使用注意版本限制，version 20+
 2.RecyclerView GridLayoutManager 居中问题 
	/**
	 * RecyclerView item 居中处理
	 */
	public class ItemOffsetDecoration extends RecyclerView.ItemDecoration {

		private int mItemOffset;

		public ItemOffsetDecoration(int itemOffset) {
			mItemOffset = itemOffset;
		}

		public ItemOffsetDecoration(@NonNull Context context, @DimenRes int itemOffsetId) {
			this(context.getResources().getDimensionPixelSize(itemOffsetId));
		}

		@Override
		public void getItemOffsets(Rect outRect, View view, RecyclerView parent,  RecyclerView.State state) {
			super.getItemOffsets(outRect, view, parent, state);
			outRect.set(mItemOffset, mItemOffset, mItemOffset, mItemOffset);
		}
	}
	
	in java :
	recyclerView.addItemDecoration(new ItemOffsetDecoration(activity, R.dimen.grid_space));
	in xml :
	android:clipToPadding="false"
	android:padding="@dimen/grid_space"





