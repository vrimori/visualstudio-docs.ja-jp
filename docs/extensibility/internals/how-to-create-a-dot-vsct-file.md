---
title: "方法: 作成します。Vsct ファイル | Microsoft Docs"
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
  - "VSCT ファイルを作成します。"
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: 作成します。Vsct ファイル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio コマンド テーブルの XML ベースの構成 \(.vsct\) ファイルを作成するいくつかの方法があります。  
  
-   新しい VSPackage を作成する、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージ テンプレートです。  
  
-   XML ベースのコマンド テーブル構成コンパイラ Vsct.exe を使用して、既存の .ctc ファイルからファイルを生成することができます。  
  
-   Vsct.exe を使用して、既存の .cto ファイルから .vsct ファイルを生成できます。  
  
-   新しい .vsct ファイルを手動で作成することができます。  
  
 このトピックでは、新しい .vsct ファイルを手動で作成する方法について説明します。  
  
### 新しい .vsct ファイルを手動で作成するには  
  
1.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動します。  
  
2.  **ファイル** \] メニューをポイント **新規**, 、\] をクリックし、 **ファイル**します。  
  
3.  **テンプレート** \] ウィンドウで、をクリックして **XML ファイル** \] をクリックし、 **開く**します。  
  
4.  **ビュー** \] メニューのをクリックして **プロパティ\] ウィンドウ** XML ファイルのプロパティを表示します。  
  
5.  **プロパティ** ウィンドウで、\[参照\] \(\[...\]\) \[スキーマ\] プロパティ\] ボタンをクリックします。  
  
6.  XSD スキーマの一覧で、vsct.xsd スキーマを選択します。 一覧にない場合、クリックして **追加** し、ローカル ドライブ上のファイルを検索します。 クリックして **OK** が終了したら。  
  
7.  XML ファイルに次のように入力します。 `<CommandTable` TAB キーを押します。 」と入力してタグを閉じる `>`します。  
  
     これには、基本的な .vsct ファイルが作成されます。  
  
8.  追加する XML ファイルの要素を入力してによる、 [VSCT スキーマ](../../extensibility/vsct-xml-schema-reference.md)します。 詳細については、「[作成します。Vsct ファイル](../../extensibility/internals/authoring-dot-vsct-files.md)」を参照してください。  
  
## コードのコンパイル  
 .Vsct ファイルをプロジェクトに追加するだけでは発生しませんしてコンパイルします。 ビルド プロセスでは、それを組み込む必要があります。  
  
### .Vsct ファイルをプロジェクトのコンパイルに追加するには  
  
1.  エディターで、プロジェクト ファイルを開きます。 プロジェクトが読み込まれている場合最初にアンロードする必要があります。  
  
2.  追加、 [ItemGroup 要素](../../msbuild/itemgroup-element-msbuild.md) VSCTCompile の要素を含む次の例で示すようにします。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 要素は常に設定する必要があります `Menus.ctmenu`します。  
  
3.  プロジェクトに .resx ファイルが含まれている場合は、次の例のように、MergeWithCTO 要素を含む埋め込まれたリソース要素を追加します。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     このマークアップを埋め込みリソースを含む ItemGroup 要素内に配置する必要があります。  
  
4.  通常という名前のパッケージ ファイルを開く *ProjectName*Package.cs または *ProjectName*エディターでの Package.vb です。  
  
5.  次の例のように、ProvideMenuResource 属性をパッケージ クラスに追加します。  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     最初のパラメーター値は、プロジェクト ファイルで定義したリソース名の属性の値に一致する必要があります。  
  
## 参照  
 [作成します。Vsct ファイル](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [方法: 既存の .Ctc ファイルから .Vsct ファイルを作成する](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [方法: 既存の .Cto ファイルから .Vsct ファイルを作成する](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)