---
title: -Build (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 070dcb383b25315e363b822da87409eb953a9ac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186411"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
指定したソリューションの構成ファイルを使用してソリューションをビルドします。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>引数  
 `SolutionName`  
 必須。 ソリューション ファイルの完全パスと名前。  
  
 `SolnConfigName`  
 必須。 `SolutionName` で指定されたソリューションのビルドに使用されるソリューション構成の名前。  
  
 /project `ProjName`  
 任意。 ソリューション内のプロジェクト ファイルのパスと名前です。 `SolutionName` フォルダーからプロジェクト ファイルへの相対パス、プロジェクトの表示名、またはプロジェクト ファイルの完全なパスと名前を入力できます。  
  
 /projectconfig `ProjConfigName`  
 任意。 指定した `/project` のビルド時に使用されるプロジェクトのビルド構成の名前。  
  
## <a name="remarks"></a>Remarks  
 このスイッチは、統合開発環境 (IDE) 内の **[ソリューションのビルド]** メニュー コマンドと同じ機能を実行します。  
  
 空白を含む文字列を二重引用符で囲みます。  
  
 エラーなどのビルドの概要情報は、**[コマンド]** ウィンドウ、または `/out` スイッチで指定された任意のログ ファイルに表示できます。  
  
 このコマンドは、最後のビルド以降に変更されたプロジェクトのみをビルドします。 ソリューション内のすべてのプロジェクトをビルドするには、[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) を使用します。  
  
## <a name="example"></a>例  
 この例では、`Debug` プロジェクトのビルド構成を使用して、`MySolution` の `Debug` ソリューション構成内でプロジェクト `CSharpConsoleApp` をビルドします。  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



