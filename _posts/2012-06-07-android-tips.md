---
layout: post
title:  Android tips
Tags: Android
---
## TextViewにマージンを設定

	TextView textView = (TextView)convertView.findViewById(R.id.title);
	RelativeLayout.LayoutParams params = (RelativeLayout.LayoutParams) textView.getLayoutParams(); // (※)
	params.setMargins(34, 0, 0, 0);
	textView.setLayoutParams(params);

※　ViewGroupがRelativeLayoutの時

## ListViewのセパレーターの設定

	_listView.setDivider(new ColorDrawable(android.R.color.black));
	_listView.setDividerHeight(1);
