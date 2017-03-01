---
title: "キーボード ショートカットをメニュー項目にバインドします |。Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 15
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
ms.openlocfilehash: e75976be74d7d0362102a2cbeb32a85d3e612c67
ms.lasthandoff: 02/22/2017

---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>メニュー項目にバインドのキーボード ショートカット
カスタム メニュー コマンドにキーボード ショートカットをバインドするにだけ、パッケージの .vsct ファイルにエントリを追加します。 このトピックでは、カスタム ボタン、メニュー項目、またはツール バー コマンドをキーボード ショートカットをマップする方法と既定のエディターのキーボード マッピングを適用またはカスタム エディターを制限する方法について説明します。  
  
 キーボード ショートカットを既存の Visual Studio のメニュー項目に割り当てるを参照してください。[識別とカスタマイズのキーボード ショートカット](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)します。  
  
## <a name="choosing-a-key-combination"></a>キーの組み合わせを選択します。  
 さまざまなキーボード ショートカットは、Visual Studio で既に使用されます。 重複するバインドを検出することは難しいとも予期しない結果になるためには、複数のコマンドを同じショートカットを割り当てる必要がありますされません。 そのため、それを割り当てる前に、ショートカットの可用性を確認することをお勧めを勧めします。  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>キーボード ショートカットの可用性を確認するには  
  
1.  **ツール/オプション/環境**ウィンドウで、**キーボード**します。  
  
2.  確認して**で新しいショートカット キーを使う**に設定されている**グローバル**します。  
  
3.  **ショートカット キーを押して**ボックスに、使用するキーボード ショートカットを入力します。  
  
     Visual Studio で、ショートカットが既に使用されている場合、**で現在使用してショートカット**ボックスは、ショートカットを現在呼び出すコマンドを表示します。  
  
4.  マップされていないものが見つかるまで、さまざまなキーの組み合わせを実行してください。  
  
    > [!NOTE]
    >  Alt キーを使用するキーボード ショートカットは、メニューを開くし、コマンドを直接実行可能性があります。 したがって、**で現在使用してショートカット**alt キーを含むショートカットを入力する際に、ボックスが空白になる場合があります。 ショートカットを閉じて、メニューが開始できなかったことを確認することができます、**オプション** ダイアログ ボックスと、キーを押します。  
  
 次の手順では、メニュー コマンドを使用して既存の vs パッケージがあることを前提としています。 この操作の説明を必要がある場合を見て[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>コマンドにキーボード ショートカットを割り当てる  
  
1.  パッケージに .vsct ファイルを開きます。  
  
2.  空の作成`<KeyBindings>`セクションの後に、`<Commands>`が存在しない場合。  
  
    > [!WARNING]
    >  ショートカット キーの詳細については、次を参照してください。 [Keybinding](../extensibility/keybinding-element.md)します。  
  
     `<KeyBindings>`セクションで、作成、`<KeyBinding>`エントリです。  
  
     設定、`guid`と`id`を起動するコマンドの属性です。  
  
     設定、`mod1`属性を**コントロール**、 **Alt**、または**Shift**します。  
  
     ショートカット キーのセクションでは、次のようになります。  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 キーボード ショートカットは、複数の&2; つのキーを必要とする場合は、設定、`mod2`と`key2`属性です。  
  
 ほとんどの状況で**Shift**によって既にキーを押して大文字や記号を入力するほとんどの英数字キーになるので、2 つ目の修飾子を指定せず使用しないで必要があります。  
  
 仮想キー コードでは、それらのなどのファンクション キーに関連付けられている文字がない特殊なキーにアクセスできます。 および**BACKSPACE**キー。 詳細については、次を参照してください。[仮想キー コード](http://go.microsoft.com/fwlink/?LinkID=105932)します。  
  
 コマンドは、Visual Studio で利用可能なエディター、設定、`editor`属性を`guidVSStd97`します。  
  
 コマンドは、カスタム エディターでのみ使用可能な設定、`editor`属性によって生成されたカスタム エディターの名前を[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]パッケージ テンプレートには、VSPackage を作成したときに、カスタム エディターが含まれています。 名前の値を検索するファイルの場所、`<Symbols>`については、「、`<GuidSymbol>`ノードが`name`属性が、"`editorfactory`"。これは、カスタム エディターの名前です。  
  
## <a name="example"></a>例  
 この例では、という名前のコマンドにキーボード ショートカット CTRL + ALT + C をバインド`cmdidMyCommand`という名前のパッケージで`MyPackage`します。  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>例  
 この例では、という名前のコマンドにキーボード ショートカット CTL + B をバインド`cmdidBold`という名前のプロジェクトで`TestEditor`します。 コマンドは、他のエディターではなく、カスタム エディターでのみ使用可能です。  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)
