---
title: "MSBuild 応答ファイル | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: "3"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: a9ceab64ec0009dd143f42e1b94538690780f1bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-response-files"></a>MSBuild 応答ファイル
応答 (.rsp) ファイルは、MSBuild.exe のコマンド ライン スイッチを含むテキスト ファイルです。 各スイッチを個別の行に記述することも、すべてのスイッチを 1 つの行に記述することもできます。 コメント行は **#** 記号で始まります。 **@** スイッチは、MSBuild.exe に別の応答ファイルを渡すために使用されます。  
  
 自動応答ファイルは、プロジェクトをビルドする際に MSBuild.exe が自動的に使用する特別な .rsp ファイルです。 この MSBuild.rsp ファイルは、MSBuild.exe と同じディレクトリに配置する必要があります。それ以外の場合は検出されません。 このファイルを編集して、MSBuild.exe に既定のコマンド ライン スイッチを指定できます。 たとえば、プロジェクトをビルドする際に毎回同じロガーを使用する場合は、**/logger** スイッチを MSBuild.rsp に追加することで、プロジェクトがビルドされるたびに MSBuild.exe がそのロガーを使用するようになります。  
  
## <a name="see-also"></a>関連項目  
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [Command-Line Reference (コマンド ライン リファレンス)](../msbuild/msbuild-command-line-reference.md)