---
title: ファイルのビルド ファイル
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45a0e4822bc9b6d20bd2cf63d664e6cba97c77bf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951301"
---
# <a name="build-actions"></a>ビルド アクション

Visual Studio プロジェクト内のすべてのファイルに、ビルド アクションがあります。 ビルド アクションでは、プロジェクトのコンパイル時にファイルに行われる処理が制御されます。

> [!NOTE]
> このトピックは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac については、[Visual Studio for Mac でのビルド アクション](/visualstudio/mac/build-actions)に関するページを参照してください。

## <a name="set-a-build-action"></a>ビルド アクションを設定する

ファイルのビルド アクションを設定するには、**[プロパティ]** ウィンドウでファイルのプロパティを開きます。その場合、**ソリューション エクスプローラー**でファイルを選択し、**Alt** + **Enter** キーを押します。 または、**ソリューション エクスプローラー**でファイルを右クリックし、**[プロパティ]** を選択します。 **[プロパティ]** ウィンドウの **[詳細設定]** セクションで、**[ビルド アクション]** の横にあるドロップダウン リストを使用して、ファイルのビルド アクションを設定します。

![Visual Studio のファイルのビルド アクション](media/build-actions.png)

## <a name="build-action-values"></a>ビルド アクションの値

C# および Visual Basic プロジェクト ファイルのビルド アクションをいくつか以下に示します。

* **なし** - ファイルはいかなる形でもビルドに含まれません。 この値は、"ReadMe" ファイルなどのドキュメント ファイルで使用できます。
* **コンパイル** - ファイルはソース ファイルとしてコンパイラに渡されます。
* **コンテンツ** - **コンテンツ**としてマークされたファイルは、<xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType> を呼び出すことでストリームとして取得できます。 ASP.NET プロジェクトの場合、展開時に、これらのファイルはサイトの一部として含まれます。
* **埋め込みリソース** - ファイルは、アセンブリに埋め込むリソースとしてコンパイラに渡されます。 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> を呼び出し、アセンブリからファイルを読み取ることができます。
* **AdditionalFiles** - 入力として C# または Visual Basic コンパイラに渡される、ソース以外のテキスト ファイル。 このビルド アクションは主に、コードの品質を確認するためにプロジェクトによって参照される、[アナライザー](../code-quality/roslyn-analyzers-overview.md)への入力を提供するために使用されます。 詳細については、[追加ファイルの使用](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic コンパイラ オプション](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [ビルド アクション (Visual Studio for Mac)](/visualstudio/mac/build-actions)