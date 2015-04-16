---
layout: post
title: ButterKnife 简单使用
---
 
 对于 Android 开发来说，最烦人的莫过于 N 多的 `findViewByid` 和 `setOnClickListener`，这里介绍一个 Android 开发者都十分熟悉的 View 注入框架 [ButterKnife][1]
 
 `注意： 目前 github 有两个版本，maven 6.1.0 和 github mater 代码不一致， maven 引入方式为 inject ，而 github master 引入方式为 bind ,本文示例代码使用的是 github master 代码 `
 
 此外，引入 ButterKnife  library [Eclipse][2] 和 [Android studio][3] 引入还需另外配置
 
 
 **目前 ButterKnife 支持如下事件回调和资源初始化** 
 
 * `android.widget.CompoundButton` setOnCheckedChangeListener
 * `android.view.View` setOnClickListener & setOnFocusChangeListener & setOnLongClickListener & setOnTouchListener
 * `android.widget.TextView` setOnEditorActionListener & addTextChangedListener
 * `android.widget.AdapterView<?>` setOnItemClickListener & setOnItemLongClickListener & setOnItemSelectedListener
 * `android.support.v4.view.ViewPager` setOnPageChangeListener
 * `ResourceBool` & `ResourceColor` & `ResourceDimen` & `ResourceDrawable` & `ResourceInt` & `ResourceString` 

 **部分示例代码**

* Activity 

```java
public class ButterKnifeActivity extends BaseActivity {
    // 6.1.0 初始化
    //@InjectView(R.id.text_view) TextView textView;
	//@InjectView(R.id.editText) EditText editText;
	//@InjectView(R.id.button) Button button;
	//@InjectView(R.id.list_view) ListView listView;

	// 控件初始化
	@FindView(R.id.text_view) TextView textView;
	@FindView(R.id.editText) EditText editText;
	@FindView(R.id.button) Button button;
	@FindView(R.id.list_view) ListView listView;
	
	// 资源初始化 
	@ResourceString(R.string.app_name) String textString;
	
	private SimpleAdapter adapter;
	
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.butter_knife_layout);
		// 引入 ButterKnife 注解
		// ButterKnife.inject(this); // 6.1.0
		ButterKnife.bind(this);

		textView.setText("ButterKnife TextView");
		editText.setText(textString);
		button.setText("ButterKnife Button");
		
		adapter = new SimpleAdapter(this);
		listView.setAdapter(adapter);
		
	}
	
	// 按钮单击
	@OnClick(R.id.button)
	void btnClick() {
		showShortToast("butter knife inject button click listener");
	}
	
	// 按钮长按
	@OnLongClick(R.id.button)
	boolean onLongClick(){
		showShortToast("ButterKnife Long Click ...");
		return true;
	}
	
	// list item 单击
	@OnItemClick(R.id.list_view)
	void onListItemClick(int position){
		showShortToast("position..." + adapter.getItem(position).toString());
	}
	
	// list item 长按
	@OnItemLongClick(R.id.list_view)
	boolean onListLongClick(){
		showShortToast("ButterKnife List Long Click ...");
		return true;
	}
	
	@Override
	protected void onDestroy() {
		// TODO Auto-generated method stub
		super.onDestroy();
		// 销毁
		// ButterKnife.reset(this); // 6.1.0
		ButterKnife.unbind(this);
	}
}
```

* Fragment

 ```java
public class ButterKnifeFragment extends Fragment {
  @InjectView(R.id.button1) Button button1;
  @InjectView(R.id.button2) Button button2;
 
  @Override View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
    View view = inflater.inflate(R.layout.button_knife_fragment, container, false);
    ButterKnife.inject(this, view);
    // TODO Use "injected" views...
    return view;
  }
}
 ```

* ViewHolder

```java
    ......
    
    public View getView(int position, View convertView, ViewGroup parent) {
        .....
    }

	static class ViewHolder{
		// 6.1.0
		//@InjectView(R.id.id_text) TextView idTv;
		//@InjectView(R.id.name_text) TextView nameTv;
		//@InjectView(R.id.sex_text) TextView sexTv;
		//@InjectView(R.id.age_text) TextView ageTv;
		
		//7.x
		@FindView(R.id.id_text) TextView idTv;
		@FindView(R.id.name_text) TextView nameTv;
		@FindView(R.id.sex_text) TextView sexTv;
		@FindView(R.id.age_text) TextView ageTv;
		
		public ViewHolder(View view) {
			// 6.1.0
			// ButterKnife.inject(this, view);
			// 7.x
			ButterKnife.bind(this, view);
		}
	}

```



[1]:https://github.com/JakeWharton/butterknife
[2]:http://jakewharton.github.io/butterknife/ide-idea.html
[3]:http://jakewharton.github.io/butterknife/ide-eclipse.html
