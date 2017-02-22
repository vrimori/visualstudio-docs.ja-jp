---
title: "IDebugMethodField::GetThis | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetThis"
helpviewer_keywords: 
  - "IDebugMethodField::GetThis メソッド"
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

含むオブジェクトの `this` \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] の `Me`\) にメソッドのポインターを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### パラメーター  
 `ppClass`  
 \[入力\] [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) に「」ポインターを返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 オブジェクト指向言語ではクラスの現在のインスタンス化に暗黙的なポインターでは通常です。  これは C\#\/C\+\+ の `this` と [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] の `Me` と呼ばれます。  
  
## 参照  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)