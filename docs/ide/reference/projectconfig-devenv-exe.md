---
title: -ProjectConfig (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 11
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 02fd2a046b7b4070fa4e1903bd13772c518a7207
ms.lasthandoff: 02/22/2017

---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
`/project` 引数で指定されたプロジェクトをビルド、消去、リビルド、または展開する際に適用されるプロジェクトのビルド構成を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>引数  
 /build  
 `/project` `ProjName` で指定されたプロジェクトをビルドします。  
  
 /clean  
 ビルド時に作成されたすべての中間ファイルと出力ディレクトリを消去します。  
  
 /rebuild  
 `/project` `ProjName` で指定されたプロジェクトを消去してからビルドします。  
  
 /deploy  
 ビルドまたはリビルド後にプロジェクトを展開することを指定します。  
  
 `SolnConfigName`  
 必須です。 `SolutionName` で指定されたソリューションに適用されるソリューション構成の名前。  
  
 `SolutionName`  
 必須です。 ソリューション ファイルの完全パスと名前。  
  
 /project `ProjName`  
 省略可能です。 ソリューション内のプロジェクト ファイルのパスと名前です。 `SolutionName` フォルダーからプロジェクト ファイルへの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全なパスと名前を入力できます。  
  
 /projectconfig `ProjConfigName`  
 省略可能です。 指定した `/project` に適用されるプロジェクトのビルド構成の名前。  
  
## <a name="remarks"></a>コメント  
  
-   `devenv /build`、/`clean`、`/rebuild`、または `/deploy` コマンドの一部として `/project` スイッチとともに使用する必要があります。  
  
-   空白を含む文字列を二重引用符で囲みます。  
  
-   エラーなどのビルドの概要情報は、[**コマンド**] ウィンドウ、または `/out` スイッチで指定された任意のログ ファイルに表示できます。  
  
## <a name="example"></a>例  
 この例では、`Debug` プロジェクトのビルド構成を使用して、`MySolution` の `Debug` ソリューション構成内でプロジェクト `CSharpConsoleApp` をビルドします。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
