---
title: メニュー コマンドのローカライズ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8eb9e566f4f5916961a95a1c61f8fdcbb689f1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876218"
---
# <a name="localize-menu-commands"></a>メニュー コマンドをローカライズします。
ローカライズされたを作成してメニューやツールバーのローカライズされたテキストを行うことができます *.vsct*ファイルし、ローカライズ *.resx*に組み込むこと、VSPackage とし、プロジェクト ファイルの更新ファイル、変更します。  
  
 インストール エクスペリエンスをローカライズする方法については、次を参照してください。[ローカライズ VSIX パッケージ](../extensibility/localizing-vsix-packages.md)します。  
  
## <a name="localize-command-names"></a>コマンド名をローカライズします。  
 Vspackage では、メニュー コマンドやツールバーのボタンがで定義されて、 *.vsct*ファイル。  
  
1. **ソリューション エクスプ ローラー**の名前を変更、 *.vsct*ファイルから*filename.vsct*に*filename.en US.vsct*します。  
  
2. コピーを作成*filename.en US.vsct*各ローカライズ言語。  
  
    各コピーを名前*ファイル名 {。ロケール} .vsct*ここで、 *{ロケール}* は特定のカルチャの名前です。 カルチャ名の値の一覧は、次を参照してください。 [Microsoft によって割り当てられたロケール Id](/windows/uwp/publish/supported-languages)します。  
  
    これら*ファイル名。Locale.vsct*ファイル、パッケージのローカライズされたメニュー テキストが含まれます。  
  
3. 各を開きます。*ファイル名。Locale.vsct*テキストをローカライズするファイル。  
  
   1. 変更、 [ButtonText](../extensibility/buttontext-element.md)要素が特定の言語のとして適切な値します。  
  
   2. ローカライズされたアイコンを提供する場合は、変更、[ビットマップ](../extensibility/bitmap-element.md)ターゲット ファイルを指定する値。  
  
      次の例では、コマンドのファミリ ツリー エクスプ ローラー ツール ウィンドウを開きを英語とスペイン語のボタンのテキストを示します。  
  
      [*FamilyTree.en US.vsct*]  
  
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
  
    [*FamilyTree.es ES.vsct*]  
  
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
  
## <a name="localize-other-text-resources"></a>その他のテキストのリソースをローカライズします。  
 コマンド名以外の文字列リソースがリソースで定義されている (*.resx*) ファイル。  
  
1.  名前を変更*VSPackage.resx*に*VSPackage.en US.resx*します。  
  
2.  コピーを作成、 *VSPackage.en US.resx*ファイルごとにローカライズされた言語です。  
  
     各コピーを名前*VSPackage {。ロケール} .resx*ここで、 *{ロケール}* は特定のカルチャの名前です。  
  
3.  名前を変更*Resources.resx*に*各カルチャ用 US.resx*します。  
  
4.  コピーを作成、*各カルチャ用 US.resx*ファイルごとにローカライズされた言語です。  
  
     各コピーを名前*リソースです {。ロケール} .resx*ここで、 *{ロケール}* は特定のカルチャの名前です。  
  
5.  各を開きます。 *.resx*の特定の言語およびカルチャに適切な値は文字列を変更するファイル。 次の例では、ツール ウィンドウのタイトル バーのローカライズされたリソースの定義を示します。  
  
     [*各カルチャ用 US.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [*Resources.es ES.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporate-localized-resources-into-the-project"></a>ローカライズされたリソースをプロジェクトに組み込む  
 変更する必要があります、 *assemblyinfo.cs*ファイルとローカライズされたリソースを組み込むプロジェクト ファイル。  
  
1.  **プロパティ**ノード**ソリューション エクスプ ローラー**オープン*assemblyinfo.cs*または*assemblyinfo.vb*エディターで。  
  
2.  次のエントリを追加します。  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     これは既定の言語として英語 (米国) 設定します。  
  
3.  プロジェクトをアンロードします。  
  
4.  エディターでプロジェクト ファイルを開きます。  
  
5.  検索、`ItemGroup`要素を含む`EmbeddedResource`要素。  
  
6.  `EmbeddedResource`要素を呼び出す*VSPackage.en US.resx*、置換、`ManifestResourceName`を持つ要素を`LogicalName`に設定されている要素`VSPackage.en-US.Resources`、次のようにします。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  ローカライズされた言語ごとに、コピー、`EmbeddedResource`要素`VsPackage.en-US`、設定、 **Include**属性と**LogicalName**コピーでは、次に示すように、対象のロケールの要素例です。  
  
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
  
     これは、メイン アセンブリでは、および各言語のリソース アセンブリを作成します。 展開プロセスをローカライズする方法の詳細については、次を参照してください[ローカライズ VSIX パッケージ。](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>関連項目  
 [メニューとコマンドを拡張します。](../extensibility/extending-menus-and-commands.md)   
 [Menucommand とOleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [グローバル化およびアプリケーションのローカライズ](../ide/globalizing-and-localizing-applications.md)