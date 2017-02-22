---
title: "ボタンの再利用可能なグループを作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ボタン グループ、Vspackage を作成します。"
  - "Vspackages にある、再利用可能なボタンのグループを作成します。"
  - "ボタン、再利用可能なグループを作成します。"
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 44
caps.handback.revision: 44
ms.author: "gregvanl"
manager: "ghogen"
---
# ボタンの再利用可能なグループを作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コマンド グループは、常にまとめてメニューまたはツールバーに表示されるコマンドのコレクションです。 .Vsct ファイルの CommandPlacements セクション内の別の親メニューに代入することによって、任意のコマンド グループを再利用できます。  
  
 コマンドのグループには、ボタン、通常が含まれますが、他のメニューやコンボ ボックスに含めることもできます。  
  
### ボタンの再利用可能なグループを作成するには  
  
1.  という名前の VSIX プロジェクトを作成する `ReusableButtons`です。 詳細については、「[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)」を参照してください。  
  
2.  プロジェクトを開いたら、という名前のカスタム コマンド項目テンプレートを追加 **ReusableCommand**します。**ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。**新しい項目の追加** ダイアログ ボックスに移動 **Visual c\#\/機能拡張** を選択して **にカスタム コマンド**します。**名** ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する **ReusableCommand.cs**します。  
  
3.  .Vsct ファイルの Symbols セクションに移動し、グループ、およびプロジェクトのコマンドを含む GuidSymbol 要素を検索します。 それは guidReusableCommandPackageCmdSet を名前必要があります。  
  
4.  次の例のように、グループに追加する各ボタンについて、IDSymbol を追加します。  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="ReusableCommandId" value="0x0100" /> <IDSymbol name="SecondReusableCommandId" value="0x0200" /> </GuidSymbol>  
    ```  
  
     既定では、コマンドの項目テンプレートがという名前のグループを作成 **MyGroup** と各 IDSymbol エントリと共に、指定された名前を持つボタンをクリックします。  
  
5.  Groups\] セクションでは、シンボルで示されているものと同じ GUID と ID の属性を持つグループ要素を作成します。 既存のグループを使用しても次の例のように、コマンド テンプレートによって提供されるエントリを使用します。 このグループが表示される、 **ツール** メニュー  
  
    ```xml  
    <Groups> <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/> </Group> </Groups>  
    ```  
  
### 再利用するためのボタンのグループを作成するには  
  
1.  コマンドまたはメニューの定義内の親として、グループを使用するか、コマンドまたはメニューを CommandPlacements セクションを使用して、グループ内に配置することで、グループで、コマンド プロンプトまたはメニューを配置できます。  
  
     ボタン\] セクションでは、その親のグループを持つボタンを定義またはパッケージ テンプレートによって提供されるボタンを使用して次の例で示すようにします。  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> <Icon guid="guidImages" id="bmpPic1" /> <Strings> <ButtonText>Invoke ReusableCommand</ButtonText> </Strings> </Button>  
    ```  
  
2.  ボタンは、1 つ以上のグループに表示される必要があります、CommandPlacements」セクションで、コマンドのセクションの後に配置する必要がありますのエントリを作成します。 位置は、目的のボタンに合わせて CommandPlacement 要素の GUID と ID の属性を設定し、設定の GUID とその親要素の ID、ターゲット グループの次の例で示すように。  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> </CommandPlacement> </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  優先順位フィールドの値では、新しいコマンド グループ内のコマンドの位置を決定します。 要素は、これらの項目の定義で設定を上書き CommandPlacement で優先順位を設定します。 高い優先順位値を持つコマンドの前に、低い優先順位値を持つコマンドが表示されます。 重複する優先順位の値が許可されますを同じ優先度の値を持つコマンドの相対位置を保証できない順序、 **devenv \/setup** コマンドは、最終版を作成、レジストリからインターフェイスを一貫性のあるできない可能性があります。  
  
### メニューにボタンの再利用可能なグループを配置するには  
  
1.  内のエントリを作成、 `CommandPlacements` セクションです。 GUID と ID の設定、 `CommandPlacement` 、グループの要素とターゲットの場所の親の GUID と ID を設定します。  
  
     CommandPlacements セクションは、「コマンド」セクションの直後に配置する必要があります。  
  
    ```xml  
    <CommandTable> ... <Commands>... </Commands> <CommandPlacements>... </CommandPlacements> ... </CommandTable>  
    ```  
  
     1 つ以上のメニュー コマンドのグループを含めることできます。 親メニューであることが、作成したいずれかのによって提供される [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(説明するよう ShellCmdDef.vsct または SharedCmdDef.vsct\)、または別の VSPackage で定義されているいずれかです。 親レイヤーの数は、親メニューが最終的に接続されている限り、無制限 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] または VSPackage で表示されるショートカット メニューにします。  
  
     次の例では、グループに、 **ソリューション エクスプ ローラー** ツールバーで、その他のボタンの右側にします。  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/> </CommandPlacement> </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup" priority="0x605"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" /> </CommandPlacement> </CommandPlacements>  
  
    ```