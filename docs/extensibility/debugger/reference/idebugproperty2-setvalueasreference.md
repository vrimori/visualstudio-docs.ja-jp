---
title: "IDebugProperty2::SetValueAsReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsReference"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsReference メソッド"
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定された参照の値にこのプロパティの値を設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```c#  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### パラメーター  
 `rgpArgs`  
 \[入力\] マネージ コード内のプロパティの setter に渡す引数の配列。  プロパティの setter が引数を使用しないか[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)このオブジェクトがこのようなプロパティの setter を参照 `rgpArgs` はnull 値。  通常このパラメーターには null 値です。  
  
 `dwArgCount`  
 \[入力\] `rgpArgs` の配列の引数の数。  
  
 `pValue`  
 \[入力\] 参照このプロパティを設定して使用する値への [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) のオブジェクトの形式で。  
  
 `dwTimeout`  
 \[入力\] ミリ秒の値を設定するために使用するのに要する。  一般的な値は `INFINITE` です。  これにより使用可能な評価ができる時間に影響します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合は通常次のいずれかを返します :  
  
|エラー|Description|  
|---------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|参照から値を設定することはできません。|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|値はこのプロパティがメソッドを示すように設定することはできません。|  
|`E_SETVALUE_VALUE_IS_READONLY`|値は読み取り専用で設定できません。|  
|`E_NOTIMPL`|このメソッドは実装されていません。|  
  
## 参照  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)