---
title: 要素の文字列 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b62df361a965028240316c14da4c8c9ee8e578c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997703"
---
# <a name="strings-element"></a>文字列要素
文字列要素を含める必要がありますが、少なくとも**ButtonText**子要素。 その他のすべての子要素は省略可能です。 などの無効な XML 文字 '&' と '<' のエンティティとしてコーディングする必要があります ('&amp;'と'&lt;' など)。  
  
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
|language|任意。 Language ="."です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|ButtonText|このフィールドとコマンド定義の次の 5 つのテキスト フィールドをさまざまなメニューに表示されるテキストを指定できます。 既定で、`ButtonText`フィールド メニュー コント ローラーに表示されます。 `ButtonText`他のテキスト フィールドが空白の場合にフィールドが既定値にもになります。 `ButtonText`場合でも、他のテキスト フィールドが指定されたフィールドを空白にすることはできません。|  
|ToolTipText|`ToolTipText`フィールドは、メニュー項目のツールヒントに表示されるテキストを指定します。<br /><br /> 場合、`ToolTipText`フィールドが空白で、`ButtonText`フィールドを使用します。|  
|MenuText|`MenuText`フィールドは、メインのメニューやサブメニュー、ショートカット メニューで、ツールバー上にある場合、コマンドが表示されるテキストを指定します。 場合、`MenuText`フィールドが空で、統合開発環境 (IDE) を使用して、`ButtonText`フィールド。 `MenuText`フィールドは、ローカライズも使用できます。<br /><br /> ショートカット メニューで、`MenuText`フィールドは、IDE のショートカット メニューをカスタマイズできるように、ショートカット メニュー ツールバーに表示される名前です。 したがって、;、ショートカット メニューの名前で特定します。たとえば、"Shortcut"ではなく「ウィジェット パッケージ ショートカット メニュー」を使用します。<br /><br /> 場合、`MenuText`フィールドが指定されていない、`ButtonText`フィールドを使用します。|  
|CommandName|`CommandName`フィールドで、キーボード カテゴリで表示されるテキストを指定します、**コマンド** タブで、**カスタマイズ** ダイアログ ボックス (をクリックして**カスタマイズ**上、**ツール**メニュー)。|  
|用|英語`CanonicalName`フィールドに入力できる英語のテキストで、コマンドの名前を指定します、**コマンド**ウィンドウで、メニュー項目を実行します。 IDE は、文字、数字、アンダー スコア、または埋め込まれたピリオドではない任意の文字を除外します。 このテキストに連結し、`ButtonText`コマンドを定義するフィールド。 たとえば、**新しいプロジェクト**上、**ファイル**メニュー コマンド、File.NewProject になります。<br /><br /> 場合、英語`CanonicalName`フィールドが指定されていない、IDE を使用、`ButtonText`フィールド、および文字、数字、アンダー スコア、および埋め込みの期間を除くすべてをタップします。 たとえば、ボタンのテキスト"& 定義コマンド..."になります DefineCommands、アンパサンド、領域、および、省略記号が削除されます。<br /><br /> 場合、`TextChanges`フラグが指定されており、コマンドのテキストが変更で認識される対応するコマンド、**コマンド**ウィンドウが変更されません正規の形式、元のまま`ButtonText`または英語。`CanonicalName`フィールド。|  
|LocCanonicalName|`LocCanonicalName`フィールドの動作と同じ、英語`CanonicalName`フィールドでは、コマンドのローカライズされたテキストを指定するができるようにします。 正規の両方のフィールドを指定できます。 IDE がだけに入力したテキストを解析するため、**コマンド**ウィンドウとコマンドを英語以外のテキストと英語の両方で同じコマンドで関連付けることができます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Button 要素](../extensibility/button-element.md)|ユーザーが対話できる要素を定義します。|  
|[Menu 要素](../extensibility/menu-element.md)|1 つのメニュー項目を定義します。|  
|[Combo 要素](../extensibility/combo-element.md)|コンボ ボックスに表示されるコマンドを定義します。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)