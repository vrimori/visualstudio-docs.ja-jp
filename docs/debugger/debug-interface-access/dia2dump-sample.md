---
title: Dia2dump サンプル |Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93c103387ff2acd7b041fc103bc519e9ac166593
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859647"
---
# <a name="dia2dump-sample"></a>Dia2dump サンプル

Dia2dump サンプルは、Microsoft デバッグ インターフェイス アクセス ソフトウェア開発キット (DIA SDK) を使用して情報を PDB ファイルを照会する方法を示しています。

Dia2dump サンプルでは、Visual Studio と共にインストールされ、ソリューションとソース ファイルが含まれています。 コンパイル済み実行可能ファイルは、コマンドラインから実行します。 プログラム全体のデータベース (.pdb) ファイルの内容を表示できるまたは該当するセクションだけです。

## <a name="install-the-sample"></a>サンプルをインストールします。

選択すると、サンプルがインストールされている、 **C++ によるデスクトップ開発**Visual Studio インストーラーにワークロード。 Visual Studio をインストールして、特定のワークロードと個々 のコンポーネントを選択する方法については、次を参照してください。 [Visual Studio のインストール](../../install/install-visual-studio.md)します。

インストールすると、サンプルは、\DIA SDK\Samples\DIA2Dump という名前のサブディレクトリに、Visual Studio インストール ディレクトリです。

## <a name="build-the-sample"></a>このサンプルをビルドする

既定では、インストール ディレクトリは、保護されたディレクトリは。 つまり、ビルドし、この場所で、サンプル ソリューションを編集して、管理者特権での開発者コマンド プロンプトまたは Visual Studio のインスタンスを使用する必要があります。 ビルドを簡素化するには、最初のサンプル ディレクトリから、ドキュメント フォルダー内のフォルダーなどの別のディレクトリにファイルをコピーし、サンプルをビルドし、お勧めします。

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Dia2Dump サンプルを Visual Studio でビルドするには

1. Visual Studio で DIA2Dump.sln ファイルを開きます。 ソリューションを別のディレクトリにコピーしていない場合は、管理者特権を持つ Visual Studio を再起動する求めることがあります。

1. **ソリューション エクスプ ローラー**、Dia2Dump プロジェクト (ソリューションではなく) を選択します。

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](/cpp/ide/working-with-project-properties)」を参照してください。

1. 開く、**構成プロパティ** > **C/C++** > **全般**プロパティ ページ。

1. **追加のインクルード ディレクトリ**プロパティは、ドロップダウン コントロールを選択しを選択**編集**します。

1. **追加のインクルード ディレクトリ** ダイアログ ボックスで、編集 フィールドを入力、`$(VSInstallDir)DIA SDK\include`ディレクトリ。 コンパイラが dia2.h ファイルを見つけることを保証するには、このディレクトリを追加します。 **[OK]** を選択して変更を保存します。

1. 選択**OK**プロジェクト プロパティに変更を保存します。

1. **ビルド**] メニューの [選択**ソリューションのリビルド**します。 既定では、Visual Studio はデバッグのソリューション ディレクトリのサブディレクトリにあるサンプルのデバッグ バージョンを構築します。

1. Visual Studio を閉じます。

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Dia2Dump サンプルをコマンドラインでビルドするには

1. 開発者コマンド プロンプト ウィンドウでは、サンプル ファイルをコピーしたディレクトリに移動します。 に別のディレクトリをサンプルをコピーしていない場合は、管理者特権 (管理者として実行) を使用する必要があります開発者コマンド プロンプト ウィンドウ。

1. コマンドを入力して`nmake makefile`dia2dump.exe の既定のデバッグ構成を作成します。

## <a name="run-the-dia2dump-sample"></a>Dia2Dump サンプルを実行します。

Msdia 依存 Dia2Dump.exe*バージョン*.dll COM サーバーのサービスを提供します。 Visual Studio 2015 と Visual Studio 2017 では、バージョンは、msdia140.dll です。 場合、msdia*バージョン*.dll COM サーバーは初期化されていません、dia2dump.exe 使用前に登録する必要があります。 DIA SDK ディレクトリの bin サブディレクトリを x86 が含まれていますが、DLL のバージョン。 バージョンを x64 のアーキテクチャのマシンは、bin\amd64 で ARM 用のバージョンであり bin\arm します。 Dll を登録するに、管理者特権での開発者コマンド プロンプト ウィンドウを開き、コンピューターのアーキテクチャのバージョンが含まれているディレクトリに変更します。 コマンドを入力して`regsvr32 msdia140.dll`COM サーバーを登録します。

### <a name="to-run-the-sample"></a>サンプルを実行するには

1. コマンド プロンプトを開き、作成した dia2dump.exe を含むディレクトリに変更します。

1. コマンドを入力して`dia2dump filename`場所*filename*検査する PDB ファイルの名前を指定します。 PDB ファイルが別のディレクトリ内にある場合とファイルの完全なパスを使用して、 *filename*します。 このコマンドは、PDB ファイル内のすべてのデータを表示します。

1. Dia2Dump には、選択した情報のみを表示するには、他のオプションがあります。 使用して、`dia2dump -?`コマンドを使用可能なオプションをすべて一覧表示します。

## <a name="see-also"></a>関連項目

- [Visual Studio プロジェクトのポート、移行、アップグレード](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
