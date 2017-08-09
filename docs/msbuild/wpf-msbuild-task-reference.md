---
title: "WPF MSBuild タスク リファレンス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 124466bbe97d1e8510e6a1966e2c900a07555b74
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild タスク リファレンス
Windows Presentation Foundation (WPF) のビルド プロセスは、マークアップのコンパイルやリソースのプロセスを含む追加のビルド タスクのセットで Microsoft ビルド エンジン (MSBuild) を拡張します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 ソース リソースのセットをアセンブリに埋め込まれるリソースとして分類します。 ローカライズできないリソースは、メイン アプリケーション アセンブリに埋め込まれます。ローカライズ可能なリソースは、サテライト アセンブリに埋め込まれます。  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 プロジェクト内の少なくとも 1 つの [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] ページが、そのプロジェクトでローカルに宣言されている型を参照している場合に、アセンブリを生成します。 生成されたアセンブリは、ビルド処理が完了した後、またはビルド処理が失敗した場合に削除されます。  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 現在の [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] ランタイムのディレクトリを返します。  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 ローカライズできない [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] プロジェクト ファイルをコンパイルされたバイナリ形式に変換します。  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 同じプロジェクト内で型を参照する [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] ファイルの 2 回目のマークアップのコンパイルを実行します。  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 1 つ以上の [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] バイナリ形式ファイルのローカリゼーション属性とコメントを、アセンブリ全体で単一のファイルにマージします。  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 1 つ以上のリソース (.jpg、.ico、.bmp、バイナリ形式の [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]、その他の種類の拡張子) を .resources ファイルに埋め込みます。  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 ソース [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ファイルに含まれるすべての [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 要素をローカライズするために、一意識別子 (UID) をチェック、更新、または削除します。  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] プロジェクトのビルド時に **\<hostInBrowser />** 要素をアプリケーション マニフェスト (*プロジェクト名*.exe.manifest) に追加します。  
  
## <a name="see-also"></a>関連項目  
 [MSBuild](../msbuild/msbuild.md)
