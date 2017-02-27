---
title: "IDebugProperty3::CreateObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::CreateObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::CreateObjectID"
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプロパティの一意の ID を他のすべてのプロパティ間で一意であることを確認するために作成します。  
  
## 構文  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはデバッグ セッションの管理にこのプロパティは他のすべてのプロパティ間で識別されることを確認するときに呼び出されます。  プロパティを処理 \(DE\) するデバッグ エンジンではこのメソッドが識別されます。  DE このメソッドがをサポートしていない場合 `E_NOTIMPL` を返します。  
  
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) のメソッドが呼び出された場合に `CreateObjectID` で作成される一意の ID が破棄されています ; これはこのプロパティを識別するために必要なの終了を示します。  
  
> [!NOTE]
>  この一意の ID を取得するメソッドがありません。したがって `CreateObjectID` のメソッドを呼び出すとしますが一意な ID に必要な処理を行うことができます。  
  
## 参照  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)