---
title: "IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::GetServerFriendlyName"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetServerFriendlyName"
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

サーバーの表示名を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### パラメーター  
 `pbstrName`  
 \[入力\] サーバーの表示名を返します。  
  
> [!NOTE]
>  呼び出し元は文字列の解放を管理します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 ユーザーはサーバーの場合このメソッドによって返される名前はサーバーの完全名です。  自動起動サーバーの場合名前はサーバーが実行しているコンピューターの場合です。  
  
 コンピューター方向の名前は[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)