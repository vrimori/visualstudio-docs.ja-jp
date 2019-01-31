---
title: ShowWebBrowser コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a46f37f93340226c669df5db59745af17c7b2464
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958889"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser コマンド

指定した URL を統合開発環境 (IDE: Integrated Development Environment) の内部または外部の Web ブラウザーのウィンドウに表示します。

## <a name="syntax"></a>構文

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>引数
 `URL`

 必須です。 Web サイトの URL (Uniform Resource Locator)。

## <a name="switches"></a>スイッチ
 /new

 任意。 Web ブラウザーの新しいインスタンスにページが表示されるように指定します。

 /ext

 任意。 IDE の外部にある既定の Web ブラウザーにページが表示されるように指定します。

## <a name="remarks"></a>コメント
 **ShowWebBrowser** コマンドのエイリアスは **navigate** または **nav** です。

## <a name="example"></a>例
 次の例では、IDE の外部にある Web ブラウザーに Microsoft Docs のホーム ページを表示します。 既に Web ブラウザーのページが開いている場合は、そのページを使用します。それ以外の場合は、新しいインスタンスが起動します。

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>「

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)