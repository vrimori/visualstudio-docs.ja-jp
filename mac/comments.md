---
title: コメント
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 0d49896a3c265dfdc5a25c46e80de498adfffb07
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="comments"></a>コメント

コードをデバッグしたり、コードで実験したりするとき、一時的に、あるいは長期間、コードのブロックにコメントを付けると便利です。 

コード ブロック全体にコメントを付けるには:

* コードを選択し、コンテキスト メニューから **[行コメントの切り替え]** を選択します。

OR

* 選択したコードで `cmd + /` キー バインドを使用します。

いずれの方法も、コード セクションにコメントを付けるか、コメントを解除するために利用できます。 C# ファイルの場合、行コメントのレベルを追加できます。レベルを追加すると、実際のコメントを維持しながら、コード領域にコメントを付けたり、コメントを解除したりできます。 

 ![複数レベルのコメント](media/source-editor-image8.png)

コメントは、将来、コードを利用するかもしれない開発者のためにコードを記録しておく意味でも役立ちます。 以上の作業は通常、複数行コメントという形態で行われます。これは各言語で次のように追加されます。

**C#**

``` cs
/*
 This is a multi-line
 comment in C#
*/
```
**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```
