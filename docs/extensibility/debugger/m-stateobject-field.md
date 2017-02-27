---
title: "m_stateObject フィールド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "m_stateObject フィールドに、タスク クラス [.NET Framework のデバッグ エンジン]"
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# m_stateObject フィールド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アクションを使用するデータを表すオブジェクト。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.field assembly object m_stateObject  
```  
  
## 解説  
 これは、 `state` 内のパラメーター、 <xref:System.Threading.Tasks.Task.%23ctor%2A> コンス トラクターです。 バッキング フィールドも、 <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> プロパティです。  
  
## 参照  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)