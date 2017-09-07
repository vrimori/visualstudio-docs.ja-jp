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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 13910907c6041884cc0a1414fd0bfd82757a7639
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="localizing-menu-commands"></a>メニュー コマンドのローカライズ
メニューのローカライズされたテキストを指定することができ、ツールバーがローカライズされた .vsct ファイルを作成するコマンドしローカライズされた .resx ファイルを VSPackage とするために、プロジェクト ファイルを更新し、変更を反映します。  
  
 インストール エクスペリエンスをローカライズする方法については、次を参照してください。 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)です。  
  
## <a name="localizing-command-names"></a>コマンド名のローカライズ  
 Vspackage では、メニュー コマンドやツールバーのボタンは、.vsct ファイルで定義されます。  
  
1.  **ソリューション エクスプ ローラー**から .vsct ファイルの名前を変更*filename*に .vsct *filename*.en US.vsct です。  
  
2.  コピーを作成*filename*.en-US.vsct 各ローカライズ言語。  
  
     各コピーの名前を付けます*filename*.*ロケール*.vsct、場所*ロケール*特定のカルチャの名前を指定します。 カルチャ名の値の一覧は、次を参照してください。 [Microsoft によるロケール Id 割り当て](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx)です。  
  
     これら*filename*.*ロケール*.vsct ファイルは、パッケージのローカライズされたメニュー テキストが含まれます。  
  
3.  各を開きます*filename*。 *。ロケール*.vsct ファイルをテキストをローカライズします。  
  
    1.  変更、 [ButtonText](../extensibility/buttontext-element.md)要素の値に応じて、特定の言語です。  
  
    2.  提供する場合はローカライズされたアイコン、変更、[ビットマップ](../extensibility/bitmap-element.md)ターゲット ファイルを指定する値。  
  
     次の例では、コマンドのファミリ ツリー エクスプ ローラー ツール ウィンドウを開きを英語とスペイン語のボタンのテキストを示します。  
  
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
  
## <a name="localizing-other-text-resources"></a>その他の文字列リソースのローカライズ  
 コマンド名以外の文字列リソースは、リソース (.resx) ファイルで定義されます。  
  
1.  VSPackage.en US.resx VSPackage.resx に変更します。  
  
2.  ローカライズされた言語ごとに VSPackage.en US.resx ファイルのコピーを作成します。  
  
     各コピー VSPackage の名前を付けます。*ロケール*.resx、場所*ロケール*特定のカルチャの名前を指定します。  
  
3.  各 US.resx に Resources.resx を変更します。  
  
4.  ローカライズされた言語ごとに各 US.resx ファイルのコピーを作成します。  
  
     各コピー リソースの名前を付けます。*ロケール*.resx、場所*ロケール*特定のカルチャの名前を指定します。  
  
5.  特定の言語とカルチャの適切な文字列値を変更するには、各 .resx ファイルを開きます。 次の例は、ツール ウィンドウのタイトル バーのローカライズされたリソース定義を示しています。  
  
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
  
## <a name="incorporating-localized-resources-into-the-project"></a>ローカライズされたリソースをプロジェクトに組み込むこと  
 Assemblyinfo.cs ファイルとローカライズされたリソースを組み込むプロジェクト ファイルを変更する必要があります。  
  
1.  **プロパティ**内のノード**ソリューション エクスプ ローラー**、assemblyinfo.cs または assemblyinfo.vb をエディターで開きます。  
  
2.  次のエントリを追加します。  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     これは既定の言語として英語 (米国) 設定します。  
  
3.  プロジェクトをアンロードします。  
  
4.  エディターで、プロジェクト ファイルを開きます。  
  
5.  検索、`ItemGroup`要素を含む`EmbeddedResource`要素。  
  
6.  `EmbeddedResource` VSPackage.en US.resx を呼び出す要素を交換して、`ManifestResourceName`を持つ要素を`LogicalName`に設定されている要素`VSPackage.en-US.Resources`、次のようにします。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  ローカライズされた言語ごとに、コピー、 `EmbeddedResource` VsPackage.en 英語 (米国)、およびセットの要素、 **Include**属性と**LogicalName**コピーでは、次に示すように、対象のロケールの要素例です。  
  
8.  ローカライズされた各`VSCTCompile`要素を追加、`ResourceName`要素を指す`Menus.ctmenu`次の例で示すように、します。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. プロジェクト ファイルを保存し、プロジェクトの再読み込みします。  
  
10. プロジェクトをビルドします。  
  
     これは、メインのアセンブリ、および各言語のリソース アセンブリを作成します。 展開プロセスをローカライズする方法の詳細については、次を参照してください[VSIX パッケージのローカライズ。](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [MenuCommand と OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)
