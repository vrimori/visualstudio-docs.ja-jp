---
title: "メニュー コマンドのローカライズ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 11
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 869a1c878a591e6b755fc1311132e159d38ffe8f
ms.lasthandoff: 02/22/2017

---
# <a name="localizing-menu-commands"></a>メニュー コマンドのローカライズ
メニューのローカライズされたテキストを入力して、ツールバーは、コマンドのローカライズされた .vsct ファイルを作成して、ローカライズされた .resx ファイルを変更を組み込むための VSPackage とプロジェクト ファイルを更新します。  
  
 インストール作業をローカライズする方法については、次を参照してください。 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)します。  
  
## <a name="localizing-command-names"></a>コマンド名をローカライズします。  
 Vspackages にある、メニュー コマンドやツール バー ボタンは、.vsct ファイルで定義されます。  
  
1.  **ソリューション エクスプ ローラー**から .vsct ファイルの名前を変更*filename*に .vsct *filename*.en US.vsct です。  
  
2.  コピーを作成*filename*各 .en US.vsct ローカライズ言語です。  
  
     名前を各コピー *filename*.*ロケール*.vsct、ここで*ロケール*特定のカルチャの名前を指定します。 カルチャ名の値の一覧は、次を参照してください。 [Microsoft によるロケール Id 割り当て](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx)します。  
  
     これら*filename*.*ロケール*.vsct ファイル、パッケージのローカライズされたメニュー テキストが記載されます。  
  
3.  各を開きます*filename*。* 。ロケール*.vsct ファイルのテキストをローカライズします。  
  
    1.  変更、 [ButtonText](../extensibility/buttontext-element.md)要素値は、特定の言語用に適切にします。  
  
    2.  ローカライズされたアイコンを入力する場合は、変更、[ビットマップ](../extensibility/bitmap-element.md)ターゲット ファイルを指定する値。  
  
     次の例では、コマンドのファミリ ツリー エクスプ ローラー ツール ウィンドウを開いてを英語とスペイン語のボタンのテキストを示します。  
  
     [FamilyTree.en US.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Family Tree Explorer</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
     [FamilyTree.es ES.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Explorar el arbol genealogico</ButtonText>  
      </Strings>  
    </Button>  
  
    ```  
  
## <a name="localizing-other-text-resources"></a>その他の文字列リソースをローカライズします。  
 コマンド名以外の文字列リソースは、リソース (.resx) ファイルで定義されます。  
  
1.  VSPackage.en US.resx VSPackage.resx に変更します。  
  
2.  ローカライズされた言語ごとに VSPackage.en US.resx ファイルのコピーを作成します。  
  
     VSPackage 各コピーの名前を付けます。*ロケール*.resx、ここで*ロケール*特定のカルチャの名前を指定します。  
  
3.  各 US.resx を Resources.resx を変更します。  
  
4.  ローカライズされた言語ごとに各 US.resx ファイルのコピーを作成します。  
  
     各コピーのリソースの名前を付けます。*ロケール*.resx、ここで*ロケール*特定のカルチャの名前を指定します。  
  
5.  特定の言語およびカルチャに適した文字列値を変更するには、各 .resx ファイルを開きます。 次の例では、ツール ウィンドウのタイトル バーのローカライズされたリソースの定義を示します。  
  
     [各 US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>ローカライズされたリソースをプロジェクトに組み込む  
 Assemblyinfo.cs ファイルとローカライズされたリソースを組み込むようにプロジェクト ファイルを変更する必要があります。  
  
1.  **プロパティ**内のノード**ソリューション エクスプ ローラー**、assemblyinfo.cs または assemblyinfo.vb をエディターで開きます。  
  
2.  次のエントリを追加します。  
  
    ```c#  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     これは既定の言語として英語 (米国) 設定します。  
  
3.  プロジェクトをアンロードします。  
  
4.  エディターでプロジェクト ファイルを開きます。  
  
5.  検索、`ItemGroup`を含む要素`EmbeddedResource`要素。  
  
6.  `EmbeddedResource` VSPackage.en US.resx を呼び出して要素の置換、`ManifestResourceName`を持つ要素を`LogicalName`に設定されている要素`VSPackage.en-US.Resources`、次のようにします。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  ローカライズされた言語ごとに、コピー、 `EmbeddedResource` VsPackage.en 英語 (米国)、およびセットの要素、 **Include**属性と**LogicalName**次の例のように、対象のロケールのコピーの要素。  
  
8.  ローカライズされた各`VSCTCompile`要素を追加、`ResourceName`が指す要素`Menus.ctmenu`次の例のように、します。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. プロジェクト ファイルを保存し、プロジェクトの再読み込みします。  
  
10. プロジェクトをビルドします。  
  
     これは、メインのアセンブリ、および各言語のリソースのアセンブリを作成します。 展開プロセスをローカライズする方法の詳細については、次を参照してください[VSIX パッケージのローカライズ。](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [MenuCommand と OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [グローバリゼーションとローカリゼーション](http://msdn.microsoft.com/Library/9a59696b-d89b-45bd-946d-c75da4732d02)
