---
title: '方法: MSBuild.exe を使用してソリューション内の特定のターゲットをビルドする | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bdc5d824d802916c38ef0267dae0de85e8814e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533539"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>方法 : MSBuild.exe を使用してソリューション内の特定のターゲットをビルドする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: MSBuild.exe を使用して、ソリューションで特定のターゲットのビルド](https://docs.microsoft.com/visualstudio/msbuild/how-to-build-specific-targets-in-solutions-by-using-msbuild-exe)します。  
  
  
MSBuild.exe 使用して、ソリューション内の特定のプロジェクトの特定のターゲットをビルドできます。  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>ソリューション内の特定のプロジェクトの特定のターゲットをビルドするには  
  
1.  コマンド ラインで、`MSBuild.exe <SolutionName>.sln` と入力します。ここで `<SolutionName>` は実行するターゲットを含んでいるソリューションのファイル名に対応します。  
  
2.  **/t** スイッチの後ろに、*ProjectName*:*TargetName* という形式でターゲットを指定します。  
  
## <a name="example"></a>例  
 次の例では、`NotInSlnFolder` プロジェクトの `Rebuild` ターゲットを実行してから、`NewFolder` ソリューション フォルダーにある `InSolutionFolder` プロジェクトの`Clean` ターゲットを実行します。  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>関連項目  
 [Command-Line Reference (コマンド ライン リファレンス)](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)   
 [MSBuild](msbuild.md)  
 [MSBuild の概念](../msbuild/msbuild-concepts.md)


