---
title: "IDebugSymbolProviderDirect | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect インターフェイス"
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メタデータ インターフェイスおよびシンボルのコアに直接アクセスできるプロバイダーのシンボルを表します。  
  
## 構文  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## メソッド  
 このインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|デバッグのアドレスを持つアプリケーション ドメインの識別子を取得します。|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|シンボルのグループのモジュールについての情報を取得します。|  
|[GetCurrentModulesState](../Topic/IDebugSymbolProviderDirect::GetCurrentModulesState.md)|シンボルのプロバイダーがメンバーとしてシンボルのグループについての情報を取得します。|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|メタデータのインポートの情報を取得します。|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|デバッグ指定のアドレスのメソッドについての情報を取得します。|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|アンマネージ コードのシンボル リーダーを取得します。|  
  
## 解説  
 このインターフェイスは他のシンボルのプロバイダー インターフェイスの代わりに使用できます。  これは `CorSym` のメタデータとインターフェイスへの直接アクセスを提供します。  
  
## 必要条件  
 ヘッダー : Sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll