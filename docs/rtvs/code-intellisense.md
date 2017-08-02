---
title: "R Code Visual Studio 用の IntelliSense | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
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
ms.openlocfilehash: 359b9dc6bae84bb6d89e5f0f646c0b8fed5898ec
ms.contentlocale: ja-jp
ms.lasthandoff: 05/12/2017

---


# <a name="intellisense"></a>IntelliSense

Visual Studio の IntelliSense では、コードを入力するときに、呼び出すことのできる関数、オブジェクトのメンバー、関数の引数、[コード スニペット](code-snippets.md)に関する情報が、見える位置に表示されます。 また、入力に合わせて入力候補が表示され、Tab キーまたは Enter キーを押すと自動的に入力されます (**[詳細設定]** タブの[エディター オプション](code-editing.md#editor-options)を参照)。 IntelliSense は、エディターと[対話型ウィンドウ](interactive-repl.md)の両方で利用可能です。

![関数のシグネチャを示す IntelliSense](~/rtvs/media/intellisense-function-signature.png) 

関数または他のステートメントを入力するとき、IntelliSense は、既に入力したものによって (大文字/小文字を区別して) フィルター処理されたオート コンプリート メニューを提供します。

![IntelliSense のオート コンプリート メニュー](~/rtvs/media/intellisense-auto-complete-menu.png)

Tab (または、オプションの設定によっては Enter や Space) キーを押すと、ドロップダウンで選択した項目が挿入されます。 選択は方向キーで変更できます。 

また、IntelliSense は、R オブジェクトのメンバーの候補も提供します。
 
![IntelliSense によるオブジェクト メンバーの候補](~/rtvs/media/intellisense-auto-complete-r-objects.png)
 
Esc キーを押すとメニューは消えます。 Ctrl + Space キーを押すと再び表示できます。

関数呼び出しの開始 `(` を入力すると、終了 `)` が挿入され、前述したようにシグネチャ ヘルプが表示されます。

![IntelliSense が示す関数のシグネチャ ヘルプ](~/rtvs/media/intellisense-function-signature.png)

Esc キーを押すとポップアップは表示されなくなります。関数シグネチャの場合は、Ctrl + Shift + Space キーを押すと再び表示されます。

> [!Tip]
> パラメーターのヘルプによって下にあるテキストが見えなくなる場合は (ファイル エディターの場合のように)、Ctrl キーを押し続けるとパラメーターのヘルプ テキストが半透明になります。

## <a name="intellisense-for-user-defined-functions-and-variables"></a>ユーザー定義の関数および変数に対する IntelliSense

IntelliSense は、同じファイルのユーザー定義関数に (名前 - パラメーターの入力候補を含め) 適用されます。

![ユーザー定義関数に対する IntelliSense](~/rtvs/media/intellisense-same-file-functions.png)

![ユーザー定義関数に対する IntelliSense のパラメーター候補](~/rtvs/media/intellisense-parameter-completion.png)

また、IntelliSense は、同じファイルと現在のセッションの変数にも対応します。

![IntelliSense の変数の入力候補](~/rtvs/media/intellisense-variable-completion.png)

> [!Note]
> 対話型ウィンドウでは、IntelliSense は現在の R セッションの名前のみを考慮し、プロジェクト内のファイルを無視します。

## <a name="code-suggestions"></a>コードの提案

余白に電球 (スマート タグと呼ばれます) が表示されたときは、Visual Studio がよく使われるアクションに使用できるショートカットがあることを提案しています。 たとえば、エディターで `library` ステートメントを含む行をポイントすると、電球マークが表示されます。 電球を選択すると、使用可能なオプションが表示されます。

![エディターでの R のスマート タグ](~/rtvs/media/intellisense-smart-tags.png)

