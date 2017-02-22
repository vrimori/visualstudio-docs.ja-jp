---
title: "m_children フィールド | Microsoft Docs"
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
  - "m_children フィールド ContingentProperties クラス [.NET Framework のデバッグ エンジン]"
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# m_children フィールド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このタスクに登録されている子タスクの一覧。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## 解説  
 タスクの実行中に、タスクを実行するスレッドのみはこの配列にアクセスする必要があります。  
  
 タスクが完了した場合、他のスレッドには何も追加したり、そこから削除するがいない限り、このフィールドにアクセスすることができます。  
  
## 参照  
 [ContingentProperties クラス](../../extensibility/debugger/contingentproperties-class-internal-members.md)