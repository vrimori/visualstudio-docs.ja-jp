---
title: "ContingentProperties クラスの内部メンバー | Microsoft Docs"
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
  - "ContingentProperties クラス [.NET Framework のデバッグ エンジン]"
  - "デバッグ エンジンは、ContingentProperties クラス [.NET Framework]"
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# ContingentProperties クラスの内部メンバー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

その他のプロパティを含む、 <xref:System.Threading.Tasks.Task> オブジェクトです。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこれらの内部メンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## メンバー  
  
### フィールド  
  
|名前|説明|  
|--------|--------|  
|[m\_children](../../extensibility/debugger/m-children-field.md)|このタスクに登録されている子タスクの一覧。|  
  
## 解説  
 .NET Framework は、必要な場合にのみ、このクラスのフィールドを初期化します。  
  
## 参照  
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)