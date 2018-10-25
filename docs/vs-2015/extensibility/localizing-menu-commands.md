---
title: メニュー コマンドのローカライズ |Microsoft Docs
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
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2584c3cdd60c130183e09d2a809ff0ee1621856d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868847"
---
# <a name="localizing-menu-commands"></a>メニュー コマンドのローカライズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

メニューのローカライズされたテキストを行うことができ、ツールバーのコマンドのローカライズされた .vsct ファイルを作成して、変更を反映する、VSPackage とし、プロジェクト ファイルの更新のローカライズされた .resx ファイル。  
  
 インストール エクスペリエンスをローカライズする方法については、次を参照してください。 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)します。  
  
## <a name="localizing-command-names"></a>コマンド名のローカライズ  
 Vspackage では、メニュー コマンドやツールバーのボタンは、.vsct ファイルで定義されます。  
  
1. **ソリューション エクスプ ローラー**から .vsct ファイルの名前を変更*filename*に .vsct *filename*.en US.vsct します。  
  
2. コピーを作成*filename*.en-US.vsct 各ローカライズ言語。  
  
    各コピーを名前*filename*.*ロケール*.vsct、場所*ロケール*は特定のカルチャの名前です。 カルチャ名の値の一覧は、次を参照してください。 [Microsoft によるロケール Id 割り当て](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx)します。  
  
    これら*filename*.*ロケール*.vsct ファイル、パッケージのローカライズされたメニュー テキストが含まれます。  
  
3. 各を開きます*filename*。 *。ロケール*.vsct ファイルをテキストをローカライズします。  
  
   1. 変更、 [ButtonText](../extensibility/buttontext-element.md)要素が特定の言語のとして適切な値します。  
  
   2. ローカライズされたアイコンを提供する場合は、変更、[ビットマップ](../extensibility/bitmap-element.md)ターゲット ファイルを指定する値。  
  
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
  
## <a name="localizing-other-text-resources"></a>その他のテキストのリソースをローカライズします。  
 コマンド名以外の文字列リソースは、リソース (.resx) ファイルで定義されます。  
  
1.  VSPackage.en US.resx VSPackage.resx に変更します。  
  
2.  ローカライズされた言語ごとに VSPackage.en US.resx ファイルのコピーを作成します。  
  
     各コピーの VSPackage の名前を付けます。*ロケール*、.resx、*ロケール*は特定のカルチャの名前です。  
  
3.  各カルチャ用 US.resx Resources.resx に変更します。  
  
4.  ローカライズされた言語ごとに各カルチャ用 US.resx ファイルのコピーを作成します。  
  
     各コピー リソースの名前を付けます。*ロケール*、.resx、*ロケール*は特定のカルチャの名前です。  
  
5.  特定の言語とカルチャに適した文字列値を変更するには、各 .resx ファイルを開きます。 次の例では、ツール ウィンドウのタイトル バーのローカライズされたリソースの定義を示します。  
  
     [各カルチャ用 US.resx]  
  
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
 Assemblyinfo.cs ファイルとローカライズされたリソースを組み込むプロジェクト ファイルを変更する必要があります。  
  
1.  **プロパティ**ノード**ソリューション エクスプ ローラー**、assemblyinfo.cs または assemblyinfo.vb をエディターで開きます。  
  
2.  次のエントリを追加します。  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     これは既定の言語として英語 (米国) 設定します。  
  
3.  プロジェクトをアンロードします。  
  
4.  エディターでプロジェクト ファイルを開きます。  
  
5.  検索、`ItemGroup`要素を含む`EmbeddedResource`要素。  
  
6.  `EmbeddedResource`を呼び出す VSPackage.en US.resx、要素を交換して、`ManifestResourceName`を持つ要素を`LogicalName`に設定されている要素`VSPackage.en-US.Resources`、次のようにします。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  ローカライズされた言語ごとに、コピー、 `EmbeddedResource` VsPackage.en 米国、およびセットの要素、 **Include**属性と**LogicalName**コピーでは、次に示すように、対象のロケールの要素例です。  
  
8.  ローカライズされた各`VSCTCompile`要素を追加、`ResourceName`要素を指す`Menus.ctmenu`次の例のようにします。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. プロジェクト ファイルを保存し、プロジェクトの再読み込みします。  
  
10. プロジェクトをビルドします。  
  
     これは、メイン アセンブリでは、および各言語のリソース アセンブリを作成します。 展開プロセスをローカライズする方法の詳細については、次を参照してください[VSIX パッケージのローカライズ。](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [MenuCommand と OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [グローバライズとローカライズ](http://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)

