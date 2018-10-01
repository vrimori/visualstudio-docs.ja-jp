---
title: MSBuild 応答ファイル | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71fdc29db3e2af66c85637648bb0703e7f7d80c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534554"
---
# <a name="msbuild-response-files"></a>MSBuild 応答ファイル
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[MSBuild 応答ファイル](https://docs.microsoft.com/visualstudio/msbuild/msbuild-response-files)します。  
  
  
応答 (.rsp) ファイルは、MSBuild.exe のコマンド ライン スイッチを含むテキスト ファイルです。 各スイッチを個別の行に記述することも、すべてのスイッチを 1 つの行に記述することもできます。 コメント行は **#** 記号で始まります。 **@** スイッチは、MSBuild.exe に別の応答ファイルを渡すために使用されます。  
  
 自動応答ファイルは、プロジェクトをビルドする際に MSBuild.exe が自動的に使用する特別な .rsp ファイルです。 この MSBuild.rsp ファイルは、MSBuild.exe と同じディレクトリに配置する必要があります。それ以外の場合は検出されません。 このファイルを編集して、MSBuild.exe に既定のコマンド ライン スイッチを指定できます。 たとえば、プロジェクトをビルドする際に毎回同じロガーを使用する場合は、**/logger** スイッチを MSBuild.rsp に追加することで、プロジェクトがビルドされるたびに MSBuild.exe がそのロガーを使用するようになります。  
  
## <a name="see-also"></a>関連項目  
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [Command-Line Reference (コマンド ライン リファレンス)](../msbuild/msbuild-command-line-reference.md)



