---
title: "DslTextTransform コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語、コマンド"
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# DslTextTransform コマンド
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DslTextTransform.cmd は、TextTransform.exe を呼び出し、一般的なオプションで実行するスクリプトです。 DslTextTransformation.cmd を使用して、夜間のビルドを自動化することができます、 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] プロジェクトです。 詳細については、次を参照してください。 [TextTransform ユーティリティを使ってファイルを生成する](../modeling/generating-files-with-the-texttransform-utility.md)です。  
  
 DslTextTransform.cmd は、次のディレクトリにあります。  
  
 **\< visual Studio SDK インストール パス>\VisualStudioIntegration\Tools\Bin**  
  
 DslTextTransform.cmd への入力として、次の引数を指定できます。  
  
-   ドメイン モデル プロジェクトの出力ディレクトリです。  
  
-   デザイナー定義がプロジェクトの出力ディレクトリです。  
  
-   テキスト テンプレート ファイルの場所。  
  
 DslTextTransform.cmd では、既定のディレクティブ プロセッサとアセンブリを使用して指定されたテキスト テンプレート ファイルを処理します。 カスタム ディレクティブ プロセッサを作成する場合は、自分を TextTransform.exe を呼び出すバッチ ファイルを作成できます。 このバッチ ファイルで、アセンブリと関連付けられているカスタム ディレクティブ プロセッサを指定することができます。