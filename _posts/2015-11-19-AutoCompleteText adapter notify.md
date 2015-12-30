---
layout: post
title: Andorid AutoCompleteText ArrayAdapter 数据更新
---

最近公司 APP 某个功能需要用到 AutoCompleteText 来进行历史搜索提醒，但是遇到一个问题就是，ArrayAdapter 数据不能像 listview ArrayAdapter 那样自动更新。

各种尝试无果，找来源码进行查看，发现里面有两个特别的方法 `add(T object)` && `insert(T object, int index) `。

`
    public void add(T object) {
        synchronized (mLock) {
            if (mOriginalValues != null) {
                mOriginalValues.add(object);
            } else {
                mObjects.add(object);
            }
        }
        if (mNotifyOnChange) notifyDataSetChanged();
    }
`


`
    public void insert(T object, int index) {
        synchronized (mLock) {
            if (mOriginalValues != null) {
                mOriginalValues.add(index, object);
            } else {
                mObjects.add(index, object);
            }
        }
        if (mNotifyOnChange) notifyDataSetChanged();
    }

`

看到这里，也就明白了。


平常用得较多的是 继承 BaseAdapter 实现，比较少的用 Android 默认的几种 adapter，同时也忽略掉了很多基础的东西，ArrayAdapter 数据最终还是个数组，所以 ArrayAdapter 数据更新和数组是一样一样的。


http://www.pocketdigi.com/20130124/981.html

http://stackoverflow.com/questions/15861017/why-cant-i-update-the-autocompletetextview-dynamically

`Do not modify the ArrayList. Modify the ArrayAdapter, using add(), insert(), and remove(). You do not need to worry about notifyDataSetChanged().

Also, I agree with Mayra -- consider using AsyncTask instead of your thread and runOnUiThread() combination.`



