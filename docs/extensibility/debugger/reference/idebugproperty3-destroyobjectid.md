---
title: "IDebugProperty3::DestroyObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::DestroyObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::DestroyObjectID"
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

他のすべてのプロパティからこのプロパティを識別する呼び出し元が気遣わないことを示すこのプロパティに関連付けられた一意の ID を破棄します。  
  
## 構文  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 \(は既にを一意に内部的に追跡するためデバッグ エンジンはプロパティの一意の ID をサポートする必要がない場合はこのメソッドの `E_NOTIMPL` を返すことができます。  
  
 一意の ID は [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) メソッドの呼び出しと呼び出し元がこのプロパティは他のすべてのプロパティ間で識別されることを確認するときに作成されます。  
  
## 参照  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)