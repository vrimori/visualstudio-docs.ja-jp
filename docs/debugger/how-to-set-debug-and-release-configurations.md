---
title: "方法: デバッグ設定し、リリース構成 |Microsoft ドキュメント"
ms.custom: H1HackMay2017
ms.date: 04/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
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
caps.latest.revision: "45"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cc63ca48f7c35c382b668d9b7c794a4905b9dac9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-debug-and-release-configurations-in-visual-studio"></a>方法: デバッグ構成と設定リリース Visual Studio での構成
Visual Studio プロジェクトでは、ご使用のプログラムに対応するリリースとデバッグ構成を個別に用意しています。 名前が示すように、デバッグ バージョンはデバッグ用、リリース バージョンは最終リリース配布用のビルドです。  
  
プログラムのデバッグ構成のコンパイルでは、シンボリック デバッグ情報が完全に含まれ、最適化は行われません。 ソース コードと生成された命令の関係は非常に複雑であり、最適化を行うとデバッグが困難になるためです。  
  
プログラムのリリース構成は、シンボリック デバッグ情報を含まず、完全に最適化されます。 デバッグ情報が .pdb ファイルに生成されることができる場合[コンパイラ オプションによって](#BKMK_symbols_release)のために使用されます。 .Pdb ファイルの作成は、後でリリース バージョンをデバッグする必要がある場合に役立ちます。  
  
ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。  
  
ビルド構成を変更することができます、**ビルド** メニュー、ツールバーで、またはプロジェクトのプロパティ ページにします。 プロジェクト プロパティ ページは、言語固有のページです。 次の手順では、メニューとツールバーからビルド構成を変更する方法を示します。 異なる言語のプロジェクトのビルド構成を変更する方法の詳細については、「参照」セクションを参照してください。  
  
## <a name="change-the-build-configuration"></a>ビルド構成を変更します。  
  
1.  **ビルド**メニューの  **Configuration Manager**選択してから、**デバッグ**または**リリース**です。  
  
2.  ツールバーで、いずれかを選択**デバッグ**または**リリース**から、**ソリューション構成**ボックスの一覧です。  
  
     ![ツールバーのビルド構成](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     このツールバーは、Express Edition では使用できません。 使用することができます、**ビルド ソリューション F6**と**デバッグ F5 の開始**構成を選択するメニュー項目。

## <a name="BKMK_symbols_release"></a>ビルドのシンボル (.pbd) ファイルを生成します。

ほとんどの種類のプロジェクトは、.pdb ファイルが両方のデバッグ用の既定で生成され、リリース ビルドが既定の設定は、特定のプロジェクトの種類と Visual Studio のバージョンによって異なります。 構成することができます、コンパイラが .pdb ファイルを生成するかどうかにデバッグ情報の種類。

> [!IMPORTANT] 
> デバッガーは、実行可能ファイルがビルドされたときに作成された .pdb ファイルと正確に一致する実行可能ファイルの .pdb ファイルのみ読み込みます (つまり .pdb ファイルはオリジナルまたはオリジナルのコピーであることが必要)。 詳細については、「 [Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

プロジェクトの種類ごとには、これらのオプションの設定の別の方法があります。

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>C# の場合、ASP.NET、または Visual Basic プロジェクトのシンボル ファイルを生成します。

C# でのデバッグ構成のプロジェクトの設定の詳細については、次を参照してください。[プロジェクト c# デバッグ構成の設定](../debugger/project-settings-for-csharp-debug-configurations.md)です。 Visual basic の場合は、次を参照してください。[ここ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)です。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックして選択**プロパティ**です。

2. 選択、**リリース**または**デバッグ**からのビルド、**構成** ボックスの一覧です。

2. 選択**ビルド**設定をクリックして、 **[詳細設定]**ボタンをクリックします。

    Visual Basic を選択する、**コンパイル**設定、および**詳細コンパイル オプション**代わりにボタンをクリックします。

3. 選択**完全**、**ポータブル**、または**pdb_only**で、**デバッグ情報**ボックスの一覧 (**を生成するデバッグ情報** Visual Basic で)。

    汎用的な形式は、.NET Core の最新のクロスプラット フォーム形式です。 オプションの詳細については、次を参照してください。[ビルドの詳細設定 ダイアログ ボックス (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)です。

    ![C# でのビルドの Pdb を生成する](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. プロジェクトをビルドします。

    シンボル ファイルは取得、実行可能ファイルまたは出力ファイルと同じフォルダーに作成されます。

### <a name="generate-symbol-files-for-a-c-project"></a>C++ プロジェクトのシンボル ファイルを生成します。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックして選択**プロパティ**です。

2. 選択、**リリース**または**デバッグ**からのビルド、**構成** ボックスの一覧です。

2. **リンカー > デバッグ**、必要なオプションを**デバッグ情報の生成**です。

    C++ でのデバッグ構成のプロジェクトの設定の詳細については、次を参照してください。 [C++ デバッグ構成の設定をプロジェクト](../debugger/project-settings-for-a-cpp-debug-configuration.md)です。

4. プログラム データベース ファイルの生成のオプションを構成します。

    ほとんどの C++ プロジェクトで既定値は`$(OutDir)$(TargetName).pdb`、出力フォルダーに .pdb ファイルを生成します。

    ![C++ でビルドの Pdb を生成する](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. プロジェクトをビルドします。

    シンボル ファイルは取得、実行可能ファイルまたは出力ファイルと同じフォルダーに作成されます。
  
## <a name="see-also"></a>参照  
 [Visua Studio デバッガーでのシンボル (.pdb) ファイルおよびソース ファイルを指定します。](../debugger/debugger-settings-and-preparation.md)  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)   
 [デバッグ プロジェクト構成およびリリース プロジェクト構成](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)