---
title: "IDebugPointerObject::Dereference | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::Dereference"
helpviewer_keywords: 
  - "IDebugPointerObject::Dereference メソッド"
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

オブジェクトを指すに取得します。  
  
## 構文  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### パラメーター  
 `dwIndex`  
 \[入力\] オブジェクトの先頭から A の単純なバイト オフセットが指すします。  
  
 `ppObject`  
 \[入力\] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) を表すオブジェクトをオフセットが指すオブジェクトにそれを返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  このオブジェクトが他のオブジェクトを指していない場合は E\_FAIL を返します。  
  
## 解説  
 指すクラスや構造体などのプリミティブ型またはより複雑な型を指定できます。オブジェクト。  
  
## 参照  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)