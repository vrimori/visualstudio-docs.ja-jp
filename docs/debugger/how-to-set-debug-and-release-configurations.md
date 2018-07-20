---
title: デバッグ設定し、リリース構成 |Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.builds
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea27fdccaadc70f22d9c9c02d75ddef98a11be13
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153099"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>デバッグ設定し、リリース Visual Studio での構成
Visual Studio プロジェクトでは、ご使用のプログラムに対応するリリースとデバッグ構成を個別に用意しています。 名前が示すように、デバッグ バージョンはデバッグ用、リリース バージョンは最終リリース配布用のビルドです。  
  
プログラムのデバッグ構成のコンパイルでは、シンボリック デバッグ情報が完全に含まれ、最適化は行われません。 ソース コードと生成された命令の関係は非常に複雑であり、最適化を行うとデバッグが困難になるためです。  
  
プログラムのリリース構成は、シンボリック デバッグ情報を含まず、完全に最適化されます。 デバッグ、.pdb ファイルに情報を生成することができます[コンパイラ オプションによって](#BKMK_symbols_release)のために使用されます。 .Pdb ファイルを作成すると、後で、リリース バージョンをデバッグする必要がある場合に非常に便利なことができます。  
  
ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。  
  
ビルド構成を変更することができます、**ビルド**メニュー、ツールバーで、またはプロジェクトのプロパティ ページ。 プロジェクト プロパティ ページは、言語固有のページです。 次の手順では、メニューとツールバーからビルド構成を変更する方法を示します。 さまざまな言語のプロジェクトのビルド構成を変更する方法の詳細については、「参照」セクションを参照してください。  
  
## <a name="change-the-build-configuration"></a>ビルド構成を変更します。  
  
1.  **ビルド**メニューの  **Configuration Manager**を選択し、**デバッグ**または**リリース**します。  
  
2.  ツールバーで、いずれかを選択**デバッグ**または**リリース**から、**ソリューション構成**ボックスの一覧。  
  
     ![ツールバーのビルド構成](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     このツールバーは、Express Edition では使用できません。 使用することができます、**ソリューションのビルド F6**と**デバッグの開始 F5**構成を選択するメニュー項目。

## <a name="BKMK_symbols_release"></a>ビルドのシンボル (.pdb) ファイルを生成します。

ほとんどのプロジェクトの種類、.pdb ファイルは、両方のデバッグの既定値によって生成され、ビルド、リリースしますが、既定の設定は、特定のプロジェクトの種類と Visual Studio のバージョンによって異なります。 構成することができます、コンパイラが .pdb ファイルを生成するかどうか、どのようなデバッグ情報を含めます。

> [!IMPORTANT] 
> デバッガーは、実行可能ファイルがビルドされたときに作成された .pdb ファイルと正確に一致する実行可能ファイルの .pdb ファイルのみ読み込みます (つまり .pdb ファイルはオリジナルまたはオリジナルのコピーであることが必要)。 詳細については、「 [Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

各プロジェクトの種類には、これらのオプションの設定の別の方法があります。

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>C#、ASP.NET、または Visual Basic プロジェクトのシンボル ファイルを生成します。

C# でのデバッグ構成のプロジェクト設定の詳細については、次を参照してください。 [c# デバッグ構成の設定をプロジェクト](../debugger/project-settings-for-csharp-debug-configurations.md)します。 Visual basic では、次を参照してください。[このトピックの「](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)します。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックし **プロパティ**します。

2. 選択、**リリース**または**デバッグ**からビルド、**構成**一覧。

2. 選択**ビルド**設定をクリック、 **[詳細設定]** ボタンをクリックします。

    選択した Visual basic で、**コンパイル**設定と**詳細コンパイル オプション**代わりにボタンをクリックします。

3. 選択**完全**、**ポータブル**、または**pdb_only**で、**デバッグ情報**リスト ボックス (**デバッグ情報の生成** Visual Basic で)。

    移植可能な形式は、.NET Core の最新のクロス プラットフォーム形式です。 オプションの詳細については、次を参照してください。[ビルドの詳細設定 ダイアログ ボックス (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)します。

    ![C# でビルドの Pdb を生成](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. プロジェクトをビルドします。

    シンボル ファイルは取得、実行可能ファイルまたはメイン出力ファイルと同じフォルダーに作成されます。

### <a name="generate-symbol-files-for-a-c-project"></a>C++ プロジェクトのシンボル ファイルを生成します。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックし **プロパティ**します。

2. 選択、**リリース**または**デバッグ**からビルド、**構成**一覧。

2. **リンカー > デバッグ**を選択するためのオプションを必要な**デバッグ情報の生成**します。

    C++ でのデバッグ構成のプロジェクト設定の詳細については、次を参照してください。[プロジェクトの C++ デバッグ構成の設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)します。

4. プログラム データベース ファイルを生成するためのオプションを構成します。

    ほとんどの C++ プロジェクトで既定値は`$(OutDir)$(TargetName).pdb`、.pdb ファイルを出力フォルダーを生成します。

    ![C++ でのビルドの Pdb を生成](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. プロジェクトをビルドします。

    シンボル ファイルは取得、実行可能ファイルまたはメイン出力ファイルと同じフォルダーに作成されます。
  
## <a name="see-also"></a>関連項目  
 [できる Visua Studio デバッガーでシンボル (.pdb) ファイルおよびソース ファイルを指定します。](../debugger/debugger-settings-and-preparation.md)  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)
