---
title: Visual Studio での NET Framework の対象設定 | Microsoft Docs
ms.custom: ''
ms.date: 02/06/2018
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 00f6baad44b4276ed4de81a2fd55c4f5b9d1c8a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio のマルチ ターゲットの概要

Visual Studio では、プロジェクトの対象となる .NET Framework のバージョンまたはプロファイルを指定できます。 別のコンピューター上で実行するアプリケーションについては、アプリケーションが対象とする .NET Framework バージョンが、コンピューターにインストールされている .NET Framework バージョンとの互換性を持っている必要があります。

異なるバージョンのフレームワークを対象とする複数のプロジェクトを含むソリューションを作成することもできます。 フレームワークを対象にする機能は、指定したバージョンのフレームワークで利用できる機能のみをアプリケーションで使用することを保証するのに役立ちます。

> [!TIP]
> 異なるプラットフォームに対応する複数のアプリケーションを対象にすることもできます。 詳細については、[MSBuild のマルチ ターゲット](../msbuild/msbuild-multitargeting-overview.md)に関する記事をご覧ください。

## <a name="framework-targeting-features"></a>フレームワークの対象設定機能

フレームワークの対象設定機能には、次の特徴があります。

- 旧バージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を対象とするプロジェクトを開いたときに、Visual Studio でそのプロジェクトを自動的にアップグレードするか、前のバージョンを対象とした状態を維持することができます。

- プロジェクトを作成するときに、対象とする [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを指定できます。

- 既存のプロジェクトの対象となっている [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを変更できます。

- 同じソリューション内にある複数のプロジェクトのそれぞれで、異なるバージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を対象とすることができます。

- プロジェクトの対象となる [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを変更すると、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] では、参照ファイルおよび構成ファイルに対して必要な変更が加えられます。

旧バージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を対象とするプロジェクトで作業する場合は、Visual Studio は開発環境で次のような変更を動的に行います。

- **[新しい項目の追加]**、**[新しい参照の追加]**、**[サービス参照の追加]** の各ダイアログ ボックスの項目をフィルター処理して、対象のバージョンで使用できない選択肢を除外します。

- **ツールボックス**内のカスタム コントロールをフィルター処理し、対象のバージョンで使用できないコントロールを除外したり、複数のコントロールが使用可能である場合に最新のコントロールのみを表示したりします。

- IntelliSense をフィルター処理して、対象のバージョンで使用できない言語機能を除外します。

- **プロパティ** ウィンドウのプロパティをフィルター処理して、対象のバージョンで使用できないプロパティを除外します。

- メニュー オプションをフィルター処理して、対象のバージョンで使用できないオプションを除外します。

- ビルドを行う場合は、対象のバージョンに適したコンパイラのバージョンおよびコンパイラ オプションを使用します。

> [!NOTE]
> フレームワークの対象機能は、開発中のアプリケーションが正しく実行されることを保証するわけではありません。 対象のバージョンで実行できるかどうかを確認するために、アプリケーションをテストする必要があります。 .NET Framework 2.0 より前のバージョンのフレームワークを対象にすることはできません。

## <a name="selecting-a-target-framework-version"></a>対象フレームワークのバージョンの選択

プロジェクトを作成するときに、**[新しいプロジェクト]** ダイアログ ボックスで、対象の .NET Framework バージョンを選択します。 使用できる Framework のリストには、選択したテンプレートの種類に適用されるインストール済みの Framework バージョンが表示されます。 .NET Core テンプレートなどの .NET Framework を必要としないテンプレートの種類の場合、**[Framework]** ドロップダウン リストは表示されません。

![[新しいプロジェクト] ダイアログ ボックスの [Framework] ドロップダウン リスト](media/vside-newproject-framework.png)

既存のプロジェクトでは、プロジェクトのプロパティ ダイアログ ボックス内で、対象となる [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを変更できます。 詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。

## <a name="resolving-system-and-user-assembly-references"></a>システム参照およびユーザー アセンブリ参照の解決

.NET Framework の特定のバージョンを対象にするには、最初に適切なアセンブリ参照をインストールする必要があります。 [.NET ダウンロード](https://www.microsoft.com/net/download/windows) ページでさまざまなバージョンの .NET Framework の開発者向けパックをダウンロードすることができます。

**[参照の追加]** ダイアログ ボックスでは、対象の [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンに関係しないシステム アセンブリが無効にされます。その結果、それらのアセンブリをプロジェクトに誤って追加することはありません  (システム アセンブリとは、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョンの一部である .dll ファイルのことです)。対象より新しいバージョンのフレームワークに属する参照は解決されず、そのような参照に依存するコントロールを追加することはできません。 このような参照を有効にするには、プロジェクトの対象である [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を、その参照を含むバージョンに再設定します。  詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。

アセンブリ参照の詳細については、「[Resolving Assemblies at Design Time](../msbuild/resolving-assemblies-at-design-time.md)」(デザイン時のアセンブリの解決) を参照してください。

## <a name="enabling-linq"></a>LINQ の有効化

.NET Framework Version 3.5 以降を対象にする場合は、System.Core の参照と System.Linq のプロジェクトレベル インポート (Visual Basic のみ) が自動的に追加されます。 LINQ 機能を使用する場合は、[Option Infer] もオンにする必要があります (Visual Basic のみ)。 対象をそれより前のバージョンの .NET Framework に変更すると、この参照とインポートは自動的に削除されます。 詳細については、「[LINQ の使用](/dotnet/csharp/tutorials/working-with-linq)」を参照してください。

## <a name="see-also"></a>関連項目

- [マルチ ターゲット (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
