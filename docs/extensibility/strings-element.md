---
title: "要素の文字列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 86e0148d495914b1cb1c0f0d19125992930a9521
ms.lasthandoff: 02/22/2017

---
# <a name="strings-element"></a>文字列の要素
文字列要素を含める必要がありますが、少なくとも**ButtonText**子要素です。 その他のすべての子要素は省略できます。 などの無効な XML 文字 '<' と '<’ must="" be="" coded="" as="" entities=""></’>&amp;'と'&lt;' など)。  
  
 アンパサンド、テキスト文字列内では、コマンドのキーボード ショートカットを指定します。  
  
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
|language|省略可能です。 Language ="です。"です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|ButtonText|このフィールドとコマンドの定義に&5; つの次のテキスト フィールドをさまざまなメニューに表示されるテキストを指定できます。 既定では、`ButtonText`フィールド] メニューの [コント ローラーに表示されます。 `ButtonText`フィールドは既定値にもなります、他のテキスト フィールドが空白だった場合。 `ButtonText`場合でも、他のテキスト フィールドが指定されているフィールドを空白にすることはできません。|  
|ToolTipText|`ToolTipText`フィールドは、メニュー項目のツールヒントに表示されるテキストを指定します。<br /><br /> 場合、`ToolTipText`フィールドは空白になりますが、`ButtonText`フィールドを使用します。|  
|MenuText|`MenuText`フィールドは、メインのメニューでは、ツールバー、ショートカット メニューやサブメニュー上にある場合にコマンドを表示するテキストを指定します。 場合、`MenuText`フィールドが空白で、統合開発環境 (IDE) を使用して、`ButtonText`フィールドです。 `MenuText`フィールドは、ローカライズにも使用できます。<br /><br /> ショートカット メニューの`MenuText`フィールドはショートカット メニュー ツールバーには、IDE のショートカット メニューのカスタマイズを可能に表示される名前です。 そのため、特定のショートカット メニューの名前にします。たとえば、"Shortcut"ではなく「ウィジェット パッケージのショートカット メニュー」を使用します。<br /><br /> 場合、`MenuText`フィールドが指定されていない、`ButtonText`フィールドを使用します。|  
|CommandName|`CommandName`フィールドで、キーボード カテゴリに表示されるテキストを指定する、**コマンド** タブで、**カスタマイズ** ダイアログ ボックス ( をクリックして**カスタマイズ**で、**ツール** メニューの )。|  
|用|英語`CanonicalName`フィールドに入力できる英語のテキストでコマンドの名前を指定する、**コマンド**ウィンドウで、メニュー項目を実行します。 IDE は、文字、数字、アンダー スコア、または埋め込まれたピリオドではない任意の文字を除外します。 次のテキストを連結し、`ButtonText`コマンドを定義するフィールドです。 たとえば、**新しいプロジェクト**上、**ファイル**メニュー コマンド、File.NewProject になります。<br /><br /> 場合、英語`CanonicalName`フィールドが指定されていない、IDE を使用して、`ButtonText`フィールド、および文字、数字、アンダー スコア、および埋め込み期間以外のすべてをタップします。 たとえば、ボタンのテキスト「>/documents/report1.rdl」を定義するコマンド...」DefineCommands、アンパサンド、領域、および、省略記号を削除する場合になります。<br /><br /> 場合、`TextChanges`フラグを指定し、コマンドのテキストは、変更で認識される対応するコマンド、**コマンド**ウィンドウは変更されません。 元の正規の形式をそのまま`ButtonText`または英語版`CanonicalName`フィールドです。|  
|LocCanonicalName|`LocCanonicalName`フィールドは、英語を同じように動作`CanonicalName`しますが、フィールドでは、ローカライズされたコマンドのテキストを指定します。 両方の標準的なフィールドを指定できます。 IDE が単に入力したテキストを解析しているため、**コマンド**ウィンドウやコマンド、英語以外のテキストと英語の両方で同じコマンドを関連付けることができます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Button 要素](../extensibility/button-element.md)|ユーザーが対話できる要素を定義します。|  
|[Menu 要素](../extensibility/menu-element.md)|単一のメニュー項目を定義します。|  
|[コンボ要素](../extensibility/combo-element.md)|コンボ ボックスに表示されるコマンドを定義します。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
