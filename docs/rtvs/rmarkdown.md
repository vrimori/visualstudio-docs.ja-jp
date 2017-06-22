---
title: "R Tools for Visual Studio での R Markdown | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
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
ms.openlocfilehash: 972abfcfda570d66b1b15b25b16e68157fc73b81
ms.contentlocale: ja-jp
ms.lasthandoff: 05/12/2017

---

# <a name="creating-r-markdown-documents"></a>R Markdown ドキュメントの作成

R Markdown ([rmarkdown.rstudio.com](https://rmarkdown.rstudio.com/) を参照してください) は、R の分析を、高品質のドキュメント、レポート、プレゼンテーション、およびダッシュボードに変換するドキュメント形式です。

R Tools for Visual Studio には、R Markdown 項目テンプレート、エディターのサポート (エディター内の R コード用の IntelliSense など)、ファイル生成機能があります。

R Markdown を使用するには:

1. Visual Studio を閉じます。
1. (1 回のみ) [pandoc.org](http://pandoc.org/installing.html) の pandoc をインストールします。
1. Visual Studio を再起動すると、pandoc のインストールが選択されます。
1. `knitr` および `rmarkdown` パッケージをインストールします。インストールは、[インタラクティブ ウィンドウ](interactive-repl.md)から実行できます。

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. **[ファイル]、[新規]** メニュー コマンドの順に選択し、一覧から **[R Markdown]** を選択するか、ソリューション エクスプローラーでプロジェクトを右クリックし、**[R Markdown の追加]** を選択して (または **[追加]、[新しい項目]** の順に選択し、一覧から **[R Markdown]** を選択して)、新しい R Markdown ファイルを作成します。

1. 新しいファイルの既定の内容は次のとおりです。

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---
    
    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.
    
    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
    
    ```{r}
    summary(cars)
    ```
    
    You can also embed plots, for example:
    
    ```{r, echo=FALSE}
    plot(cars)
    ```
    
    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
    
    ~~~

1. 編集中にいつでも、エディターで右クリックし、**[プレビュー]** を選択します。このメニュー項目には、HTML、PDF、Microsoft Word のオプションがあります。 このプレビューから、選択したファイル形式でファイルを保存できます。

