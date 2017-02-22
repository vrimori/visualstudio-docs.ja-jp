---
title: "AsyncTaskMethodBuilder &lt; TResult &gt; 構造体の内部メンバー | Microsoft Docs"
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
  - "AsyncTaskMethodBuilder < TResult > 構造体 [.NET Framework のデバッグ エンジン]"
  - "デバッグ エンジンは、AsyncTaskMethodBuilder < TResult > 構造体 [.NET Framework]"
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# AsyncTaskMethodBuilder &lt; TResult &gt; 構造体の内部メンバー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このトピックの内部メンバーの説明、 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> クラスです。 このクラスの概要については、次を参照してください。、 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> リファレンス トピックです。  
  
 **名前空間:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこれらの内部メンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## 内部のメンバー  
  
|名前|説明|  
|--------|--------|  
|[ObjectIdForDebugger プロパティ](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|デバッガーには、このビルダーを一意に識別するために使用がオブジェクトを取得します。|  
|[m\_task フィールド](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|遅れて初期化されるタスクの構築を表します。|  
  
## 参照  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)