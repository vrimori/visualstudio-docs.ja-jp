---
title: "IDebugProperty3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3"
helpviewer_keywords: 
  - "IDebugProperty3 インターフェイス"
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProperty3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはをサポートします :  
  
-   プロパティに関連付けられている長い文字列をランダムに取得します。  
  
-   プロパティに一意の ID を関連付けます。  
  
-   プロパティにカスタム ビューアーのリストを取得します。  
  
-   発生したエラーを報告する機能はプロパティで値の設定  
  
## 構文  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)長い文字列プロパティ ID とカスタム ビューアーをサポートするために同じオブジェクトこのインターフェイスを実装する [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 実行します。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得 `IDebugProperty2` のインターフェイスでは [QueryInterface](/visual-cpp/atl/queryinterface)。  
  
## Vtable の順序でメソッド  
 `IDebugProperty2` から継承するメソッドに加え、`IDebugProperty3` インターフェイスは次のメソッドを公開します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|プロパティに関連付けられた文字列の長さを返します。|  
|[GetStringChars](../Topic/IDebugProperty3::GetStringChars.md)|ユーザーが指定したバッファーの文字列を返します。|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|このプロパティの一意の ID を作成します。|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|このプロパティの一意の ID を破棄します。|  
|[GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)|このプロパティが表示できるカスタム ビューアーの数を返します。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|このプロパティが表示できるカスタム ビューアーのリストを返します。|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|任意のいかなかったらエラー メッセージが返されますこのプロパティの値を設定します。|  
  
## 解説  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) は属性を設定するデバッグ セッションの管理者 \(SDM\) の場合に推奨される方法です。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)