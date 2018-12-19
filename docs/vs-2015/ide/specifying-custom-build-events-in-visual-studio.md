---
title: カスタム ビルド イベントの指定
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
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f2dbb785bcc3092872763d23e968cbf699603286
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067104"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Visual Studio でのカスタム ビルド イベントの指定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

カスタム ビルド イベントを指定することで、ビルドの開始前またはビルドの終了後に自動的にコマンドを実行できます。 たとえば、ビルドの開始前に .bat ファイルを実行したり、ビルドの完了後に新しいファイルをフォルダーにコピーできます。 ビルド イベントは、ビルド プロセスにおいてビルドがこれらのポイントに正常に達する場合にのみ実行します。

 使用するプログラミング言語に関する具体的な情報については、次のトピックを参照してください。

-   Visual Basic--[方法。ビルド イベントを指定する (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)。

-   VisualC#とF#--[方法。ビルド イベントを指定する (C#)](../ide/how-to-specify-build-events-csharp.md)。

-   Visual C++ -- [ビルド イベントの指定](http://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc)

## <a name="syntax"></a>構文
 ビルド イベントは、DOS コマンドと同じ構文に従いますが、マクロを使用すると、ビルド イベントをより簡単に作成することができます。 使用可能なマクロの一覧については、「[[ビルド前に実行するコマンド ライン] / [ビルド後に実行するコマンド ライン] ダイアログ ボックス](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)」を参照してください。

 最適な結果を得るには、次のような書式のヒントに従います。

-   .bat ファイルを実行するすべてのビルド イベントの前に `call` ステートメントを追加します。

     例 : `call C:\MyFile.bat`

     例 : `call C:\MyFile.bat call C:\MyFile2.bat`

-   ファイルのパスを引用符で囲みます。

     例 ([!INCLUDE[win8](../includes/win8-md.md)] の場合): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

-   改行を使用して、複数のコマンドを区切ります。

-   必要に応じて、ワイルドカードを挿入します。

     例: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`

    > [!NOTE]
    >  上記のコードの `%I` は、バッチ スクリプトでは `%%I` になります。

## <a name="see-also"></a>参照
 [コンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)[ビルド前のコマンド ライン ダイアログ ボックスのビルド後イベント](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [MSBuild の特殊文字](../msbuild/msbuild-special-characters.md)[チュートリアル。アプリケーションをビルドします](../ide/walkthrough-building-an-application.md)。
