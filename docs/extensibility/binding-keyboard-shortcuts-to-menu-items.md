---
title: "メニュー項目へのキーボード ショートカットのバインド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fe1c0bb9c3028c70e1be9df9af1de3b0804844e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>メニュー項目にバインドのキーボード ショートカット
カスタム メニュー コマンドをキーボード ショートカットをバインドするにのみ、パッケージの .vsct ファイルにエントリを追加します。 このトピックでは、カスタム ボタン、メニュー項目、またはツール バー コマンドにショートカット キーをマップする方法と、既定のエディターのキーボード マッピングを適用またはカスタム エディターを制限する方法について説明します。  
  
 キーボード ショートカットを既存の Visual Studio のメニュー項目に割り当てるを参照してください。[の識別とカスタマイズのキーボード ショートカット](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)です。  
  
## <a name="choosing-a-key-combination"></a>キーの組み合わせを選択します。  
 さまざまなキーボード ショートカットは、Visual Studio で既に使用されます。 重複するバインドを検出することは難しいとも予期しない結果になるためには、1 つ以上のコマンドを同じショートカットを割り当てる必要がありますされません。 そのため、これを割り当てる前に、ショートカットの可用性を確認することをお勧めを勧めします。  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>キーボード ショートカットの可用性を確認するには  
  
1.  **ツール/オプション/環境**ウィンドウで、**キーボード**です。  
  
2.  確認して**で使用する新しいショートカット**に設定されている**グローバル**です。  
  
3.  **ショートカット キーを押して**ボックスを使用するキーボード ショートカットを入力します。  
  
     ショートカットが Visual Studio で既に使用されている場合、**によって現在使用ショートカット**ボックスには、ショートカットを現在呼び出すコマンドを表示します。  
  
4.  マップされていないものが見つかるまで、さまざまなキーの組み合わせを試してください。  
  
    > [!NOTE]
    >  Alt キーを使用するキーボード ショートカットは、メニューを開くし、直接コマンドを実行可能性があります。 したがって、**によって現在使用ショートカット**alt キーを含むショートカットを入力するときにボックスを空白にすることがあります。 ショートカットを閉じて、メニューが開始できなかったことを確認することができます、**オプション** ダイアログ ボックスと、キーを押します。  
  
 次の手順では、メニュー コマンドを使用して既存の VSPackage があることを前提としています。 この操作の説明を必要がある場合を見て[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>コマンドをキーボード ショートカットを割り当てる  
  
1.  パッケージの .vsct ファイルを開きます。  
  
2.  空、作成`<KeyBindings>`セクションの後に、`<Commands>`が存在しない場合。  
  
    > [!WARNING]
    >  キー バインドの詳細については、次を参照してください。 [Keybinding](../extensibility/keybinding-element.md)です。  
  
     `<KeyBindings>`セクションで、作成、`<KeyBinding>`エントリです。  
  
     設定、`guid`と`id`を起動するコマンドの属性です。  
  
     設定、`mod1`属性を**コントロール**、 **Alt**、または**Shift**です。  
  
     KeyBindings セクションでは、次のようになります。  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 キーボード ショートカットは、複数の 2 つのキーを必要とする場合は、設定、`mod2`と`key2`属性。  
  
 ほとんどの状況で**Shift**文字の大文字または記号を入力するほとんどの英数字キーによって、既にキーを押してため 2 番目の修飾子を指定せず使用しないでです。  
  
 仮想キー コードでは、それらのなどのファンクション キーに関連付けられた文字がない特殊なキーにアクセスできます。 および**BACKSPACE**キー。 詳細については、次を参照してください。[仮想キー コード](http://go.microsoft.com/fwlink/?LinkID=105932)です。  
  
 コマンドは、使用できるようにする、Visual studio エディター、設定、`editor`属性を`guidVSStd97`です。  
  
 コマンドは、カスタム エディターでのみ使用可能な設定、`editor`属性によって生成されたカスタム エディターの名前を[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage を作成したときのパッケージ テンプレートには、カスタム エディターが含まれています。 名前の値を検索するファイルの場所、`<Symbols>`については、「、`<GuidSymbol>`ノードが`name`属性が、"`editorfactory`"。これは、カスタム エディターの名前です。  
  
## <a name="example"></a>例  
 この例では、という名前のコマンドをキーボード ショートカット CTRL + ALT + C をバインド`cmdidMyCommand`という名前のパッケージで`MyPackage`です。  
  
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
 この例では、という名前のコマンドをキーボード ショートカット CTL + B をバインド`cmdidBold`という名前のプロジェクトで`TestEditor`です。 コマンドは、および他のエディターではなくカスタム エディターでのみ利用できます。  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>関連項目  
 [メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)