---
title: '方法: セット デバッグ構成とリリースの構成 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 137c85f5433343327cf677ef76c1116bd6ef6821
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533802"
---
# <a name="how-to-set-debug-and-release-configurations"></a>方法 : デバッグ構成とリリース構成を設定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: デバッグ設定とリリース構成](https://docs.microsoft.com/visualstudio/debugger/how-to-set-debug-and-release-configurations)します。  
  
Visual Studio プロジェクトでは、ご使用のプログラムに対応するリリースとデバッグ構成を個別に用意しています。 名前が示すように、デバッグ バージョンはデバッグ用、リリース バージョンは最終リリース配布用のビルドです。  
  
 プログラムのデバッグ構成のコンパイルでは、シンボリック デバッグ情報が完全に含まれ、最適化は行われません。 ソース コードと生成された命令の関係は非常に複雑であり、最適化を行うとデバッグが困難になるためです。  
  
 プログラムのリリース構成は、シンボリック デバッグ情報を含まず、完全に最適化されます。 使用しているコンパイラ オプションによっては、デバッグ情報が PDB ファイル内に生成される場合があります。 PDB ファイルを作成すると、後でリリース バージョンをデバッグする際に大きく役立つことがあります。  
  
 ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。  
  
 ビルド構成を変更することができます、**ビルド**メニュー、ツールバーで、またはプロジェクトのプロパティ ページ。 プロジェクト プロパティ ページは、言語固有のページです。 次の手順では、メニューとツールバーからビルド構成を変更する方法を示します。 各種言語のプロジェクトでビルド構成を変更する方法の詳細については、以下の「関連項目」を参照してください。  
  
### <a name="to-change-the-build-configuration"></a>ビルド構成を変更するには  
  
1.  [ビルド] メニュー: をクリックして**ビルド/Configuration Manager**を選択し、**デバッグ**または**リリース**します。  
  
2.  ツールバーで、いずれかを選択**デバッグ**または**リリース**から、**ソリューション構成**ボックスの一覧。  
  
     ![ツールバーのビルド構成](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     このツールバーは、Express Edition では使用できません。 使用することができます、**ソリューションのビルド F6**と**デバッグの開始 F5**構成を選択するメニュー項目。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)   
 [デバッグ プロジェクト構成およびリリース プロジェクト構成](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)



