---
title: "要素の文字列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61d6498cafaf97033864bc31d55c257c9a3a564f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strings-element"></a>文字列の要素
文字列要素を含める必要がありますが、少なくとも**ButtonText**子要素です。 その他のすべての子要素は省略できます。 などの無効な XML 文字 '&' と '<' のエンティティとしてコーディングする必要があります ('&amp;'および'&lt;' など)。  
  
 テキスト文字列のアンパサンドは、コマンドのキーボード ショートカットを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|language|任意。 Language ="です。"です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|ButtonText|このフィールドとコマンドの定義で 5 つの次のテキスト フィールドをさまざまなメニューに表示されるテキストを指定できます。 既定では、`ButtonText`フィールド メニュー コント ローラーに表示されます。 `ButtonText`場合は、その他のテキスト フィールドは空白にフィールドが既定値にもになります。 `ButtonText`場合でも、他のテキスト フィールドが指定されたフィールドを空白にすることはできません。|  
|ToolTipText|`ToolTipText`フィールドは、メニュー項目のツールヒントに表示されるテキストを指定します。<br /><br /> 場合、`ToolTipText`フィールドは空白になりますが、`ButtonText`フィールドを使用します。|  
|MenuText|`MenuText`フィールドは、メイン メニューやサブメニュー、ショートカット メニューで、ツールバー上にある場合、コマンドに対して表示されるテキストを指定します。 場合、`MenuText`フィールドは空白、統合開発環境 (IDE) を使用して、`ButtonText`フィールドです。 `MenuText`フィールドは、ローカライズにも使用できます。<br /><br /> ショートカット メニューの`MenuText`フィールドは、ショートカット メニュー ツールバー、IDE のショートカット メニューのカスタマイズを可能に表示される名前です。 そのため、固有のもので、ショートカット メニューの名前でたとえば、"Shortcut"ではなく「ウィジェット パッケージ ショートカット メニュー」を使用します。<br /><br /> 場合、`MenuText`フィールドが指定されていない、`ButtonText`フィールドを使用します。|  
|CommandName|`CommandName`フィールドは、キーボードのカテゴリに表示されるテキストを指定、**コマンド** タブで、**カスタマイズ** ダイアログ ボックス ( をクリックして**カスタマイズ**上、**ツール**メニュー)。|  
|用|英語`CanonicalName`フィールドに入力できる英語のテキストでコマンドの名前を指定する、**コマンド**ウィンドウで、メニュー項目を実行します。 IDE は、アルファベット、数字、アンダー スコア、または埋め込まれたピリオドではない任意の文字を除外します。 このテキストに連結して、`ButtonText`コマンドを定義するフィールドです。 たとえば、**新しいプロジェクト**上、**ファイル**メニュー コマンド、File.NewProject になります。<br /><br /> 場合、英語`CanonicalName`フィールドが指定されていない、IDE を使用して、`ButtonText`フィールド、および文字、数字、アンダー スコア、および埋め込まれたピリオド以外のすべてをタップします。 たとえば、ボタン テキスト"& 定義コマンド..."になります DefineCommands、アンパサンド、領域、および、省略記号ボタンが削除されます。<br /><br /> 場合、`TextChanges`フラグが指定されており、コマンドのテキストが変更された、対応するコマンドによって認識される、**コマンド**ウィンドウが変わらない以外の場合は、元の正規の形式になります`ButtonText`または英語`CanonicalName`フィールドです。|  
|LocCanonicalName|`LocCanonicalName`フィールドは、英語を同じように動作`CanonicalName`フィールドが、ローカライズされたコマンド テキストを指定するを有効にします。 両方の標準的なフィールドを指定できます。 IDE がだけに入力したテキストを解析しているため、**コマンド**ウィンドウと関連付けられたコマンドを英語以外のテキストと英語の両方で同じコマンドを関連付けることができます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Button 要素](../extensibility/button-element.md)|ユーザーが対話する要素を定義します。|  
|[Menu 要素](../extensibility/menu-element.md)|単一のメニュー項目を定義します。|  
|[Combo 要素](../extensibility/combo-element.md)|コンボ ボックスに表示されるコマンドを定義します。|  
  
## <a name="see-also"></a>参照  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)