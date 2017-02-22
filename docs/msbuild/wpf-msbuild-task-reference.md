---
title: "WPF MSBuild Task Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WPF MSBuild task reference [WPF MSBuild], term/definition table"
  - "build tasks [WPF MSBuild], Microsoft build engine"
  - "build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources"
  - "WPF MSBuild task reference [WPF MSBuild]"
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WPF MSBuild Task Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows Presentation Foundation \(WPF\) ビルド プロセスは、追加のビルド タスクのセットによって Microsoft Build Engine \(MSBuild\) を拡張します。このタスクには、マークアップとプロセス リソースのコンパイルが含まれます。  
  
## このセクションの内容  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 ソース リソースのセットを、アセンブリに埋め込まれるリソースとして分類します。  ローカライズできないリソースは、メイン アプリケーション アセンブリに埋め込まれます。ローカライズ可能なリソースは、サテライト アセンブリに埋め込まれます。  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 プロジェクト内の少なくとも 1 つの [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] ページが、そのプロジェクトでローカルに宣言されている型を参照している場合に、アセンブリを生成します。  生成されるアセンブリは、ビルド処理が完了するか、またはビルド処理が失敗すると削除されます。  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 現在の [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] ランタイムのディレクトリを返します。  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 ローカライズできない [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] プロジェクト ファイルをコンパイル済みバイナリ形式に変換します。  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 同じプロジェクト内の型を参照する [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] ファイルに対して、2 番目のマークアップ コンパイル パスを実行します。  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 1 つ以上の [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式ファイルのローカリゼーション属性とコメントを、アセンブリ全体で単一のファイルにマージします。  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 1 つ以上のリソース \(.jpg、.ico、.bmp、バイナリ形式の [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]、その他の種類の拡張子\) を .resources ファイルに埋め込みます。  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 ソース [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルに含まれるすべての [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 要素をローカライズするために、一意識別子 \(UID\) のチェック、更新、または削除を行います。  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] プロジェクトのビルド時に、アプリケーション マニフェスト \(*projectname*.exe.manifest\) に  **\<hostInBrowser \/\>** 要素を追加するために実行されます。  
  
## 参照  
 [MSBuild](http://msdn.microsoft.com/ja-jp/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)