---
title: "R Tools for Visual Studio のヘルプ ウィンドウ | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 6644ea68ae691e8467828ff699245fef4e485971
ms.contentlocale: ja-jp
ms.lasthandoff: 05/12/2017

---


# <a name="help-in-r-tools-for-visual-studio"></a>R Tools for Visual Studio のヘルプ

R のヘルプは、Visual Studio の対話型ウィンドウに直接統合されています。 `?` コマンド (`?mtcars` など) を使用する場合、R ドキュメントのヘルプが、Visual Studio ウィンドウに表示されます。

![Visual Studio のヘルプ ウィンドウ](~/docs/rtvs/media/help-window.png)

> [!Tip]
> ヘルプ ウィンドウは、Visual Studio のその他すべてのウィンドウと同様に、好みに応じて配置およびドッキングすることができます。 「[Visual Studio のウィンドウ レイアウトをカスタマイズする](../ide/customizing-window-layouts-in-visual-studio.md)」を参照してください。
>
> また、**[R Tools] > [オプション]** メニューを選択して、**[R ヘルプ ブラウザー]** プロパティに `External` を設定し、代わりにブラウザーでヘルプの結果を開くこともできます。 [オプション](options.md)に関するページを参照してください。

ヘルプを検索するには、スペースを含む場合は検索用語を引用符で囲い、`??` コマンドを使用します。

```R
??"Motor Trend"
```

![ヘルプの検索結果](~/docs/rtvs/media/help-search1.png)

また、ヘルプ ウィンドウには、R ドキュメントの詳細な検索を直接実施できる、検索入力フィールドもあります。

![入力フィールドを使用したヘルプの検索結果](~/docs/rtvs/media/help-search2.png)

## <a name="integrated-help-lookup"></a>統合ヘルプの参照

開発者は、関数名、データセット、およびその他の要素のヘルプを入手するために R ドキュメントを検索することが多いため、R Tools for Visual Studio では、ヘルプの参照をエディターおよび対話型ウィンドウに直接統合して、プロセスを効率化しています。

- オート コンプリート操作中に F1 キーを押すと、サブ文字列に一致するヘルプの結果一覧が生成されます。
- 検索用語 (関数など) を右クリックして、**[Help on]\(ヘルプの表示\)** を選択するか、F1 キーを押して、その関数のヘルプを開きます。 また、任意の選択に対して **[Help on]\(ヘルプの表示\)** を呼び出すこともできます。

    ![コンテキスト メニューを右クリックしてヘルプを呼び出す](~/docs/rtvs/media/help-right-click.png)

> [!Tip]
> ブラウザーで統合ヘルプを開くには、**[R Tools] > [オプション]** を選択して、**[F1 Web ブラウザー]** に `External` を設定します。 [オプション](options.md)に関するページを参照してください。

## <a name="integrated-stackoverflow-search"></a>StackOverflow 検索の統合

R ドキュメントでの検索に加えて、開発者はコードを記述するときに StackOverflow を検索することが多いです。 RTVS では、このプロセスも効率化されます。 用語または選択を右クリックして、**[Search web for]\(Web で検索\)** を選択するか、Ctrl + F1 キーを押すと、Visual Studio ウィンドウ (または、**[F1 Web ブラウザー]** オプションを変更している場合はブラウザー) が開き、既定では StackOverflow を範囲とした用語の検索結果が表示されます。

![Visual Studio の Web 検索結果](~/docs/rtvs/media/help-web-search-results.png)

**[R Tools] > [オプション] > [F1 Web 検索文字列]** オプションを使用して、追加された文字列 `R site:stackoverflow` を変更できます。

![[F1 Web 検索文字列] オプションを変更する](~/docs/rtvs/media/options-dialog.png)
