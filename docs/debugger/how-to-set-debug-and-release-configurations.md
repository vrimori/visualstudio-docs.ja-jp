---
title: デバッグ設定し、リリース構成 |Microsoft Docs
ms.date: 10/05/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4c1c12409d89d88e683cd0e5b39a8d5a5459df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969773"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Visual Studio でのデバッグおよびリリース構成の設定

Visual Studio プロジェクトでは、ご使用のプログラムに対応するリリースとデバッグ構成を個別に用意しています。 デバッグでのデバッグ バージョンを最終リリース配布用のリリース バージョンをビルドします。

デバッグ構成を完全なシンボリック デバッグ情報と最適化は行われません、プログラムをコンパイルします。 ソース コードと生成された命令の関係は非常に複雑であり、最適化を行うとデバッグが困難になるためです。

プログラムのリリース構成では、シンボリック デバッグ情報がないとは完全に最適化されています。 マネージ コードと C++ コードでは、デバッグ情報を生成して .pdb ファイル、[コンパイラ オプションによって](#BKMK_symbols_release)のために使用されます。 .Pdb ファイルを作成するは、後で、リリース バージョンをデバッグする必要がある場合に役立ちます。

ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。

ビルド構成は、**[ビルド]** メニュー、ツールバー、またはプロジェクトのプロパティ ページを使用して変更できます。 プロジェクト プロパティ ページは、言語固有のページです。 次の手順では、メニューとツールバーからビルド構成を変更する方法を示します。 さまざまな言語のプロジェクトのビルド構成を変更する方法の詳細については、次を参照してください。、[も参照してください](#see-also)以下のセクション。

## <a name="change-the-build-configuration"></a>ビルド構成を変更します。

か、ビルド構成を変更します。

* **ビルド**メニューの  **Configuration Manager**を選択し、**デバッグ**または**リリース**します。

または

* ツールバーの場合は、**[ソリューション構成]** リスト ボックスから **[デバッグ]** または **[リリース]** をクリックします。

  ![ツールバーのビルド構成](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>ビルドのシンボル (.pdb) ファイルを生成 (C#、C++、Visual Basic、 F#)

シンボル (.pdb) ファイルとその内容を生成することができますに含める情報をデバッグします。 ほとんどの種類のプロジェクトのコンパイラでは、既定ではデバッグのシンボル ファイルが生成されますビルドとリリース ビルド、プロジェクトの種類と Visual Studio のバージョンが異なるその他の既定の設定中にします。

> [!IMPORTANT]
> デバッガーは、実行可能ファイルがビルドされたときに作成された .pdb ファイルと正確に一致する実行可能ファイルの .pdb ファイルのみ読み込みます (つまり .pdb ファイルはオリジナルまたはオリジナルのコピーであることが必要)。 詳細については、「[Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)」 (ビルドに使用したバイナリ ファイルと完全に一致させるために、Visual Studio でデバッガー シンボル ファイルが必要な理由) を参照してください。

各プロジェクトの種類には、これらのオプションの設定の別の方法があります。

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>C#、ASP.NET、または Visual Basic プロジェクトのシンボル ファイルを生成します。

デバッグ構成のプロジェクト設定の詳細についてC#または Visual Basic では、「[プロジェクトの設定、C#デバッグ構成](../debugger/project-settings-for-csharp-debug-configurations.md)または[プロジェクトの Visual Basic デバッグの設定構成](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)します。

1. ソリューション エクスプローラーでプロジェクトを選択します。

2. 選択、**プロパティ**アイコン (またはキーを押します**Alt + Enter**)。

3. 作業ウィンドウで次のように選択します。**ビルド**(または**コンパイル**Visual Basic で)。

4. **構成**一覧で、選択**デバッグ**または**リリース**します。

5. 選択、**詳細**ボタン (または**詳細コンパイル オプション**Visual Basic でのボタン)。

6. **デバッグ情報**リスト (または**デバッグ情報の生成**Visual Basic での一覧)、選択**完全**、 **pdb-only**、または**ポータブル**します。

   移植可能な形式は、.NET Core の最新のクロス プラットフォーム形式です。 オプションの詳細については、次を参照してください。[ビルドの詳細設定 ダイアログ ボックス (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)します。

   ![C# でビルドの Pdb を生成](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. プロジェクトをビルドします。

   コンパイラでは、実行可能ファイルまたはメイン出力ファイルと同じフォルダーにシンボル ファイルを作成します。

### <a name="generate-symbol-files-for-a-c-project"></a>C++ プロジェクトのシンボル ファイルを生成します。

1. ソリューション エクスプローラーでプロジェクトを選択します。

2. 選択、**プロパティ**アイコン (またはキーを押します**Alt + Enter**)。

3. **構成**一覧で、選択**デバッグ**または**リリース**します。

4. 作業ウィンドウで次のように選択します。**リンカー > デバッグ**、のオプションを選択**デバッグ情報の生成**します。

   C++ でのデバッグ構成のプロジェクト設定の詳細については、次を参照してください。[デバッグ構成の C++ のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)します。

5. オプションを構成**プログラム データベース ファイルの生成**します。

   ほとんどの C++ プロジェクトで既定値は`$(OutDir)$(TargetName).pdb`、.pdb ファイルを出力フォルダーを生成します。

   ![C++ でのビルドの Pdb を生成](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. プロジェクトをビルドします。

   コンパイラでは、実行可能ファイルまたはメイン出力ファイルと同じフォルダーにシンボル ファイルを作成します。

## <a name="see-also"></a>参照
 
[Visual Studio デバッガーでシンボル (.pdb) ファイルおよびソース ファイルを指定します。](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
[デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)<br/>
[C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
[C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
[Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
[方法: 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)
