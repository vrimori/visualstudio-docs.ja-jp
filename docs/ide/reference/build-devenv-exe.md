---
title: DevEnv Build スイッチ
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 777347ba36cf3443a509d1d6c8c44c23a86901e0
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764970"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

指定したソリューションの構成ファイルを使用してソリューションをビルドします。

## <a name="syntax"></a>構文

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>引数

|||
|-|-|
|*SolutionName*|必須。 ソリューション ファイルの完全パスと名前。|
|*SolnConfigName*|必須。 *SolutionName* で指定されたソリューションのビルドに使用されるソリューション構成の名前。 複数のソリューション プラットフォームが利用できる場合、**"Debug\|Win32"** など、プラットフォームも指定する必要があります。|
|/project *ProjName*|任意。 ソリューション内のプロジェクト ファイルのパスと名前です。 *SolutionName* フォルダーからプロジェクト ファイルへの相対パス、プロジェクトの表示名、プロジェクト ファイルの完全なパスと名前を入力できます。|
|/projectconfig *ProjConfigName*|任意。 指定したプロジェクトのビルド時に使用されるプロジェクトのビルド構成の名前。 複数のプロジェクト プラットフォームが利用できる場合、**"Debug\|Win32"** など、プラットフォームも指定する必要があります。|

## <a name="remarks"></a>コメント

- **/build** スイッチは、統合開発環境 (IDE) 内の **[ソリューションのビルド]** メニュー コマンドと同じ機能を実行します。

- 空白を含む文字列を二重引用符で囲みます。

- エラーなどのビルドの概要情報は、[コマンド] ウィンドウ、または **/out** スイッチで指定された任意のログ ファイルに表示できます。

- **/build** スイッチは、最後のビルド以降に変更されたプロジェクトのみをビルドします。 ソリューション内のすべてのプロジェクトをビルドするには、代わりに [/rebuild](../../ide/reference/rebuild-devenv-exe.md) を使用します。

- **プロジェクト構成が無効である**というエラー メッセージが表示された場合、**"Debug\|Win32"** など、ソリューション プラットフォームまたはプロジェクト プラットフォームを指定していることを確認してください。

## <a name="example"></a>例

次のコマンドでは、"MySolution" の "Debug" ソリューション構成内の "Debug" プロジェクト ビルド構成を使用し、プロジェクト "CSharpConsoleApp" がビルドされます。

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>関連項目

- [プロジェクトとソリューションをビルドおよびクリーンする](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)