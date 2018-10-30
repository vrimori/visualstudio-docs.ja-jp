---
title: '方法: XML スニペットを使用する |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 774a0f5639057ea5b1dc190ce475278477a7f373
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219615"
---
# <a name="how-to-use-xml-snippets"></a>方法 : XML スニペットを使用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML エディターのショートカット メニューにある次の 2 つのコマンドを使用すると、XML スニペットを呼び出すことができます。 **スニペットの挿入**コマンドは、カーソル位置にある XML スニペットを挿入します。 **ブロックの挿入**コマンドは、選択したテキストの周囲の XML スニペットをラップします。 各 XML スニペットには、スニペット型が指定されています。 スニペット型が、スニペットを使用できるかどうかを判断、**スニペットの挿入**コマンド、**ブロックの挿入**コマンド、またはその両方です。  
  
 XML スニペットがエディターに追加されると、スニペット内の編集可能なフィールドがすべて黄色で強調表示され、カーソルが最初の編集可能なフィールドに置かれます。  
  
## <a name="insert-snippet"></a>スニペットの挿入  
 次の手順にアクセスする方法について説明、**スニペットの挿入**コマンド。  
  
> [!NOTE]
>  **スニペットの挿入**コマンドも (CTRL + K、CTRL + X) のキーボード ショートカットを使用します。  
  
#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>ショートカット メニューからスニペットを挿入するには  
  
1.  XML スニペットを挿入する位置にカーソルを置きます。  
  
2.  右クリックして**スニペットの挿入**します。  
  
     使用可能な XML スニペットの一覧が表示されます。  
  
3.  マウスを使用するか、またはスニペットの名前を入力してから Tab または Enter キーを押して、スニペットを一覧から選択します。  
  
#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>IntelliSense メニューを使用してスニペットを挿入するには  
  
1.  XML スニペットを挿入する位置にカーソルを置きます。  
  
2.  **編集**メニューで、 **IntelliSense**、し、**スニペットの挿入**します。  
  
     使用可能な XML スニペットの一覧が表示されます。  
  
3.  マウスを使用するか、またはスニペットの名前を入力してから Tab または Enter キーを押して、スニペットを一覧から選択します。  
  
#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>IntelliSense の入力候補の一覧からスニペットを挿入するには  
  
1.  XML スニペットを挿入する位置にカーソルを置きます。  
  
2.  ファイルに追加する XML スニペットの名前の入力を開始します。 オートコンプリートがオンになっている場合は、IntelliSense の入力候補の一覧が表示されます。 一覧が表示されない場合は、Ctrl キーを押しながらスペース バーを押してアクティブにします。  
  
3.  入力候補の一覧から XML スニペットを選択します。  
  
4.  Tab キーを押して XML スニペットを呼び出します。  
  
> [!NOTE]
>  XML スニペットが呼び出されない場合があります。 たとえば、`xs:complexType` ノード内に `xs:element` 要素を挿入しようとした場合、エディターは XML スニペットを生成しません。 `xs:complexType` ノード内で `xs:element` 要素が使用された場合、必須の属性やサブ要素がないため、エディターに挿入するデータが存在しないことになります。  
  
#### <a name="to-insert-snippets-using-the-shortcut-name"></a>ショートカット名を使用してスニペットを挿入するには  
  
1.  XML スニペットを挿入する位置にカーソルを置きます。  
  
2.  エディターのペインに「`<`」と入力します。  
  
3.  Esc キーを押して IntelliSense の入力候補の一覧を閉じます。  
  
4.  スニペットのショートカット名を入力し、Tab キーを押して XML スニペットを呼び出します。  
  
## <a name="surround-with"></a>ブロックの挿入  
 次の手順にアクセスする方法について説明、**ブロックの挿入**コマンド。  
  
> [!NOTE]
>  **ブロックの挿入**コマンドも (CTRL + K、CTRL + S) のキーボード ショートカットを使用します。  
  
#### <a name="to-use-surround-with-from-the-context-menu"></a>コンテキスト メニューから [ブロックの挿入] を使用するには  
  
1.  XML エディターで、囲むテキストを選択します。  
  
2.  右クリックして**ブロックの挿入**します。  
  
     [ブロックの挿入] で使用可能な XML スニペットの一覧が表示されます。  
  
3.  マウスを使用するか、またはスニペットの名前を入力してから Tab または Enter キーを押して、スニペットを一覧から選択します。  
  
#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Intellisense メニューから [ブロックの挿入] を使用するには  
  
1.  XML エディターで、囲むテキストを選択します。  
  
2.  **編集**メニューで、 **IntelliSense**、し、**ブロックの挿入**します。  
  
     [ブロックの挿入] で使用可能な XML スニペットの一覧が表示されます。  
  
3.  マウスを使用するか、またはスニペットの名前を入力してから Tab または Enter キーを押して、スニペットを一覧から選択します。  
  
## <a name="using-xml-snippets"></a>XML スニペットの使用  
 XML スニペットを選択すると、カーソルの位置にコード スニペットのテキストが自動的に挿入されます。 スニペット内の編集可能なフィールドがすべて強調表示され、最初の編集可能なフィールドが自動的に選択されます。 現在選択されているフィールドは枠で囲まれます。  
  
 フィールドが選択されているときには、フィールドの新しい値を入力できます。 Tab キーを押すと編集可能なスニペットのフィールド間を順番に移動できます。Shift キーを押しながら Tab キーを押すと、逆の順序で移動できます。 フィールドをクリックすると、フィールド内にカーソルが置かれ、フィールドをダブルクリックするとフィールドが選択されます。 フィールドが強調表示されているときには、そのフィールドについて説明するツール ヒントが表示されることがあります。  
  
 編集することができるのは、特定のフィールドの最初のインスタンスだけです。 そのフィールドが強調されているときには、そのフィールドにある他のインスタンスは中抜き表示されます。 編集可能なフィールドの値を変更すると、スニペット内でフィールドが使用されているすべての場所で、そのフィールドが変更されます。  
  
 Enter キーまたは Esc キーを押すと、フィールドの編集をキャンセルしてエディターを通常の状態に戻します。  
  
 コード スニペット フィールドの設定を変更することで編集可能なコード スニペット フィールドの既定の色を変更することができます、**フォントおよび色**のウィンドウ、**オプション** ダイアログ ボックス。 詳細については、次を参照してください。[方法: エディターで変更のフォントと色](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)します。  
  
## <a name="see-also"></a>関連項目  
 [XML スニペット](../xml-tools/xml-snippets.md)   
 [方法: XML スキーマから XML スニペットを生成](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)   
 [方法 : XML スニペットを作成する](../xml-tools/how-to-create-xml-snippets.md)



