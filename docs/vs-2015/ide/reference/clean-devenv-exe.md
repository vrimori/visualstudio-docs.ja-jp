---
title: -Clean (devenv.exe) | Microsoft Docs
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
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 194081570d3b6e99966e960b3cef3163aeb945f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539073"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[-(devenv.exe) をクリーンアップ](https://docs.microsoft.com/visualstudio/ide/reference/clean-devenv-exe)します。  
  
  
すべての中間ファイルと出力ディレクトリを消去します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## <a name="arguments"></a>引数  
 `FileName`  
 必須。 ソリューション ファイルまたはプロジェクト ファイルの完全パスと名前。  
  
 /project `ProjName`  
 任意。 ソリューション内のプロジェクト ファイルのパスと名前です。 `SolutionName` フォルダーからプロジェクト ファイルへの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全なパスと名前を入力できます。  
  
 /projectconfig `ProjConfigName`  
 任意。 指定した `/project` のクリーン時に使用されるプロジェクトのビルド構成の名前。  
  
## <a name="remarks"></a>Remarks  
 このスイッチは、統合開発環境 (IDE) 内の **[ソリューションのクリーン]** メニュー コマンドと同じ機能を実行します。  
  
 空白を含む文字列を二重引用符で囲みます。  
  
 エラーを含むクリーンとビルドの概要情報は、**[コマンド]** ウィンドウ、または `/out` スイッチで指定された任意のログ ファイルに表示できます。  
  
## <a name="example"></a>例  
 最初の例では、ソリューション ファイルで指定された既定の構成を使用して、`MySolution` ソリューションを消去します。  
  
 2 番目の例では、`Debug` プロジェクトのビルド構成を使用して、`MySolution` の `Debug` ソリューション構成内でプロジェクト `CSharpConsoleApp` を消去します。  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



