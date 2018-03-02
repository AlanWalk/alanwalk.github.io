---
title: UE4中反射在C++中的应用
date: 2017-08-22
tag:
  - C++
  - UE4
category: C++
---

UE4的一大特色莫过于它的反射系统，最近在项目中有需求在C++中调用蓝图的函数或者变量，查找了一些资料，在此做下记录。

## 函数调用
```cpp
UFunction* Function = Object->FindFunction(TEXT("FunctionName"));
if (Function)
{
	struct FFunctionParms
	{
		FString Parm1;
		int32 Parm2;
	};
	FFunctionParms Parms;
	Parms.Parm1 = TEXT("Hello World!");
	Parms.Parm2 = 1;
	ProcessEvent(Function, &Parms);
}
```

## 参数调用
```cpp
UStructProperty* KeyProp = FindField<UStructProperty>(Object->GetClass(), TEXT("ShapedTextOptions")); // ShapedTextOptions为Struct的名字，需要去掉F
FShapedTextOptions* KeyPropData = KeyProp->ContainerPtrToValuePtr<FShapedTextOptions>(Object);
KeyPropData->bOverride_TextShapingMethod = 1;
```
