---
title: "ボタンの再利用可能なグループを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: "44"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c2ac175d2fd267500f19e9f22cd46d88dcc9f314
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-reusable-groups-of-buttons"></a>ボタンの再利用可能なグループを作成します。
コマンド グループは、常に一緒にメニューまたはツールバーに表示されるコマンドのコレクションです。 .Vsct ファイルの CommandPlacements セクション内の別の親メニューに代入することで、任意のコマンドのグループを再利用できます。  
  
 コマンド グループには、ボタン、通常が含まれます。 含めることができますも他のメニューまたはコンボ ボックス。  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>ボタンの再利用可能なグループを作成するには  
  
1.  という名前の VSIX プロジェクトを作成する`ReusableButtons`です。 詳細については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  プロジェクトを開いたら、という名前のカスタム コマンド項目テンプレートの追加**ReusableCommand**です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**にカスタム コマンド**です。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する**ReusableCommand.cs**です。  
  
3.  .Vsct ファイルでシンボル セクションに移動し、グループ、およびプロジェクトのコマンドを含む GuidSymbol 要素を探します。 これは、ような名前 guidReusableCommandPackageCmdSet です。  
  
4.  次の例のように、グループに追加する各ボタンの IDSymbol を追加します。  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     既定では、コマンドの項目テンプレートがという名前のグループを作成**MyGroup**と各 IDSymbol エントリと共に、指定された名前を持つボタンをクリックします。  
  
5.  グループ セクションでは、シンボルで示されているものと同じ GUID と ID の属性を持つグループ要素を作成します。 既存のグループを使用してもまたは次の例のように、コマンド テンプレートによって提供されているエントリを使用できます。 このグループが表示されます、**ツール**メニュー  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>再利用するためのボタンのグループを作成するには  
  
1.  コマンドまたはメニューの定義内の親として、グループを使用するか、コマンドまたはメニューを CommandPlacements セクションを使用して、グループ内に配置することにより、グループ内のコマンドまたはメニューを配置できます。  
  
     ボタン セクションで、グループをその親として持つボタンを定義または次の例で示すようにパッケージ テンプレートによって提供される、ボタンを使用します。  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  場合は、ボタンは、複数のグループに表示する必要があります、エントリを作成して CommandPlacements のセクションでは、コマンドのセクションの後に配置する必要があります。 ボタンを配置するのに合わせて CommandPlacement 要素の属性を GUID と ID を設定し、ように設定して、GUID とその親要素の ID、ターゲット グループの次の例に示すようにします。  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  優先順位 フィールドの値では、新しいコマンド グループ内のコマンドの位置を決定します。 優先順位は、項目の定義で設定されている要素が上書き CommandPlacement で設定します。 高い優先度値を持つコマンドの前に、低い優先度値を持つコマンドが表示されます。 重複する優先順位の値が許可されている場合を同じ優先度の値を持つコマンドの相対的な位置を保証できないため、順序、 **devenv/setup**コマンドでは、レジストリから最終的なインターフェイスを作成一貫性のあるできない可能性があります。  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>メニューのボタンの再利用可能なグループを配置するには  
  
1.  内のエントリを作成、`CommandPlacements`セクションです。 GUID と ID の設定、 `CommandPlacement` 、所属するグループの要素とターゲットの場所の親の GUID と ID を設定します。  
  
     CommandPlacements セクションでは、コマンド」セクションの直後に配置する必要があります。  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     コマンド グループは、複数のメニューに追加できます。 親メニューいずれかになります、作成したによって指定された 1 つ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)](説明するよう ShellCmdDef.vsct または SharedCmdDef.vsct)、または別の VSPackage で定義されているいずれか。 親レイヤーの数が、親メニューが最終的に接続されている限り、限られた[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]または、VSPackage によって表示されるショートカット メニューにします。  
  
     次の例では、グループに、**ソリューション エクスプ ローラー**ツールバーで、他のボタンの右側にします。  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```