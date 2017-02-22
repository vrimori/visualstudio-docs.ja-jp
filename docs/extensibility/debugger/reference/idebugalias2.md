---
title: "IDebugAlias2 | Microsoft Docs"
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
  - "IDebugAlias2 インターフェイス"
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 変数の numeric エイリアスを表し、式エバリュエーター エイリアスのアプリケーション ドメインを取得するには、\(EE\) できるようにします。  
  
## 構文  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## 実装についてのメモ  
 このインターフェイスは、マネージ デバッグ エンジン \(DE\) によって実装されます。  
  
## メソッド  
 上のメソッドだけでなく、 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|----------|--------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|アプリケーション ドメインの識別子を取得します。|  
  
## 解説  
 エイリアスは、後に \# 文字、1001 \# などの文字列形式の 10 進数です。  
  
## 必要条件  
 ヘッダー: Ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll