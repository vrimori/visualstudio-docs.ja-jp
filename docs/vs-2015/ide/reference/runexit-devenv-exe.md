---
title: -Runexit (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 86ed57dcd61e552f13694cad285c3f790fda6b2f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534655"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Runexit (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/runexit-devenv-exe)します。  
  
  
指定したプロジェクトまたはソリューションをコンパイルおよび実行してから、統合開発環境 (IDE) を閉じます。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>引数  
 `SolutionName`  
 必須。 ソリューション ファイルの完全パスと名前。  
  
 `ProjectName`  
 必須。 プロジェクト ファイルの完全パスと名前。  
  
## <a name="remarks"></a>Remarks  
 アクティブなソリューション構成に対して指定された設定に従って、指定したプロジェクトまたはソリューションをコンパイルして実行します。 このスイッチはプロジェクトまたはソリューションの実行中に IDE を最小化し、プロジェクトまたはソリューションの実行の完了後に IDE を閉じます。  
  
-   空白を含む文字列を二重引用符で囲みます。  
  
-   エラーなどの概要情報は、**[コマンド]** ウィンドウ、または `/out`スイッチで指定した任意のログ ファイルに表示できます。  
  
## <a name="example"></a>例  
 この例では、アクティブな配置構成を使用し、IDE を最小化した状態でソリューション `MySolution` を実行してから IDE を閉じます。  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



