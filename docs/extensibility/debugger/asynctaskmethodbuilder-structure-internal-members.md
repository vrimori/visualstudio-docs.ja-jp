---
title: "AsyncTaskMethodBuilder 構造体の内部メンバー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンは、AsyncTaskMethodBuilder 構造体 [.NET Framework]"
  - "AsyncTaskMethodBuilder 構造体 [.NET Framework のデバッグ エンジン]"
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# AsyncTaskMethodBuilder 構造体の内部メンバー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このトピックの内部メンバーの説明、 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> クラスです。 このクラスの概要については、次を参照してください。、 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> リファレンス トピックです。  
  
 **名前空間:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこれらの内部メンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## 内部のメンバー  
  
|名前|説明|  
|--------|--------|  
|[ObjectIdForDebugger プロパティ](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|デバッガーには、このビルダーを一意に識別するために使用がオブジェクトを取得します。|  
|[m\_builder フィールド](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|この非ジェネリック インスタンスが代行汎用ビルダー オブジェクトを表します。|  
  
## 参照  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)