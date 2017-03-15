---
title: "方法 : スタート キットを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スタート キット, 作成"
ms.assetid: ed7d1844-7c01-424a-a831-5003efe0f7bc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 方法 : スタート キットを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

スタート キットには、アプリケーションを変更または展開する方法を示す、完成したアプリケーションのコードとドキュメントが含まれています。  スタート キットの作成は、基本的には通常のプロジェクト テンプレートの作成と同じです。ただし、スタート キットにはドキュメント ファイルが含まれており、スタート キットを基にしてプロジェクトを作成するときに自動的に開くように設定されている点が異なります。  
  
## スタート キットの設計と開発  
 まず、開発するスタート キットの種類を指定し、対象となる顧客を定義します。  次に、目的に応じてプロジェクトおよびドキュメントを設計します。  
  
 サンプル アプリケーションまたはプラグインを作成する場合は、以下を実行します。  
  
-   ビルド エラーが発生しないプロジェクトを作成します。  
  
-   テンプレート コードを追加して、追加タスクを実装します \(省略可能\)。  
  
-   ドキュメントを準備します。  
  
 学習ツールを作成する場合は、以下を実行します。  
  
-   ビルド エラーが発生しないプロジェクトを作成します。  
  
-   コード スニペットや項目テンプレートなどのリソースを整理します。  
  
-   ドキュメントを準備します。  
  
## テンプレートの作成  
 プロジェクトとドキュメントが完成したら、スタート キット用のプロジェクト テンプレートを作成できます。  このプロセスは、プロジェクト テンプレートの作成とまったく同じです。  
  
 次のトピックには、テンプレートの作成に関する情報が含まれます。  
  
 [方法 : プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)  
 **テンプレートのエクスポート** ウィザードを使用してテンプレートを作成する方法について説明します。  
  
 [方法 : 既存のテンプレートを更新する](../ide/how-to-update-existing-templates.md)  
 エクスポートしたテンプレートの編集方法について説明します。  この手順によって .vstemplate ファイルを変更して、スタート キットをカスタマイズします。  
  
## 参照  
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)