---
title: メニュー項目にバインドのキーボード ショートカット |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7100e3fc6e18387cf8ef8cfdc2b485b610b3dc8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812713"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>キーボード ショートカットのメニュー項目へのバインド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

カスタム メニュー コマンドをキーボード ショートカットをバインドするには、だけパッケージの .vsct ファイルにエントリを追加します。 このトピックでは、カスタム ボタン、メニュー項目、またはツールバーのコマンドをキーボード ショートカットをマップする方法と、既定のエディターのキーボード マッピングを適用またはカスタム エディターに制限する方法について説明します。  
  
 キーボード ショートカットを既存の Visual Studio のメニュー項目に割り当てるを参照してください。[の識別とカスタマイズのキーボード ショートカット](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)します。  
  
## <a name="choosing-a-key-combination"></a>キーの組み合わせを選択します。  
 多くのキーボード ショートカットは、Visual Studio で既に使用されます。 重複するバインドを検出するが困難とも予期しない結果になるためは、1 つ以上のコマンドを同じショートカットを割り当てる必要がありますされません。 そのためは割り当てる前に、ショートカットの可用性を確認することをお勧めします。  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>キーボード ショートカットの可用性を検証するには  
  
1. **ツール/オプション/環境**ウィンドウで、**キーボード**します。  
  
2. 確認します**で新しいショートカットを使用して**に設定されている**Global**します。  
  
3. **ショートカット キーを押して**ボックスに、使用するキーボード ショートカットを入力します。  
  
    ショートカットが Visual Studio で既に使用されている場合、**によって現在使用ショートカット**ボックス ショートカットを現在呼び出すコマンドが表示されます。  
  
4. マップされていないものが見つかるまで、さまざまなキーの組み合わせをお試しください。  
  
   > [!NOTE]
   >  Alt キーを使用するキーボード ショートカットは、メニューを開くし、コマンドを直接実行可能性があります。 そのため、**によって現在使用ショートカット**alt キーを含むショートカットを入力するときにボックスを空白にすることがあります。 ショートカットを閉じて、メニューが開きますしないことを確認することができます、**オプション** ダイアログ ボックスとし、キーを押します。  
  
   次の手順では、メニュー コマンドを使用して既存の VSPackage があることを前提としています。 この操作の説明を必要がある場合について見て[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>コマンドにキーボード ショートカットを割り当てる  
  
1. パッケージの .vsct ファイルを開きます。  
  
2. 空の作成`<KeyBindings>`セクションの後に、`<Commands>`が存在しない場合。  
  
   > [!WARNING]
   >  キー バインドの詳細については、次を参照してください。 [Keybinding](../extensibility/keybinding-element.md)します。  
  
    `<KeyBindings>`セクションで、作成、`<KeyBinding>`エントリ。  
  
    設定、`guid`と`id`を起動するコマンドの属性します。  
  
    設定、`mod1`属性を**コントロール**、 **Alt**、または**Shift**します。  
  
    キー バインド セクションは、次のようになります。  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   キーボード ショートカットは、複数の 2 つのキーを必要とする場合は、設定、`mod2`と`key2`属性。  
  
   ほとんどの状況で**Shift**文字の大文字または記号を入力するほとんどの英数字キー既にキーを押すと、ために、2 つ目の修飾子を指定せず使用できません必要があります。  
  
   仮想キー コードに、たとえば、ファンクション キーに関連付けられている文字がない特殊なキーにアクセスできるように、 **BACKSPACE**キー。 詳細については、次を参照してください。[仮想キー コード](http://go.microsoft.com/fwlink/?LinkID=105932)します。  
  
   コマンドで使用できるように、Visual studio エディターの設定、`editor`属性を`guidVSStd97`します。  
  
   で、コマンドをカスタム エディターでのみ使用できるようにするには設定、`editor`属性によって生成されたカスタム エディターの名前を、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 、VSPackage を作成したときに、パッケージのテンプレートには、カスタム エディターが含まれています。 場所を名の値を検索する、`<Symbols>`のセクションを`<GuidSymbol>`ノードが`name`で属性の末尾が"`editorfactory`"。これは、カスタム エディターの名前です。  
  
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
 この例では、という名前のコマンドにキーボード ショートカット CTL + B をバインド`cmdidBold`という名前のプロジェクト`TestEditor`します。 コマンドは、および他のエディターではなく、カスタム エディターでのみ利用できます。  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>関連項目  
 [メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)

