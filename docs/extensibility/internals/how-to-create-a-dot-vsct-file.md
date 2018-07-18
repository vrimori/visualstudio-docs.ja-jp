---
title: '方法: を作成します。Vsct ファイル |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6456b0b866f08956862fa197719354bedf0ecf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132920"
---
# <a name="how-to-create-a-vsct-file"></a>方法: を作成します。Vsct ファイル  
  
Visual Studio コマンド テーブルの XML ベースの構成 (.vsct) ファイルを作成するいくつかの方法はあります。  
  
-   新しい VSPackage を作成することができます、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パッケージ テンプレート。  
  
-   XML ベースのコマンド テーブルの構成のコンパイラ、Vsct.exe を使用するには既存の .ctc ファイルからファイルを生成します。  
  
-   Vsct.exe を使用すると、既存の .cto ファイルから .vsct ファイルを生成します。  
  
-   新しい .vsct ファイルを手動で作成することができます。  
  
 このトピックでは、新しい .vsct ファイルを手動で作成する方法について説明します。  
  
### <a name="to-manually-create-a-new-vsct-file"></a>新しい .vsct ファイルを手動で作成するには  
  
1.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動します。  
  
2.  **ファイル** メニューのをポイント**新規**、クリックして**ファイル**です。  
  
3.  **テンプレート** ウィンドウで、をクリックして**XML ファイル** をクリックし、**開く**です。  
  
4.  **ビュー**  メニューのをクリックして**プロパティ ウィンドウ**XML ファイルのプロパティを表示します。  
  
5.  **プロパティ**ウィンドウで、スキーマ プロパティの参照ボタン (…) ボタンをクリックします。  
  
6.  、XSD スキーマの一覧で、vsct.xsd スキーマを選択します。 一覧にない場合、クリックして**追加**し、ローカル ドライブ上のファイルを見つけます。 をクリックして**OK**が終了したらです。  
  
7.  XML ファイルに次のように入力します。 `<CommandTable` TAB キーを押します。 」と入力してタグを閉じる`>`です。  
  
     これには、基本的な .vsct ファイルが作成されます。  
  
8.  追加する XML ファイルの要素を入力、に従って、 [VSCT スキーマ](../../extensibility/vsct-xml-schema-reference.md)です。 詳細については、次を参照してください。[作成します。Vsct ファイル](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>方法: 既存の .Ctc ファイルから .Vsct ファイルを作成する  
  
既存のコマンドテーブルの .ctc ソース ファイルから XML ベースの .vsct ファイルを作成できます。 これによりを活用すること、新しい XML ベース[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンド テーブル (VSCT) コンパイラ形式です。  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>.ctc ファイルから .vsct ファイルを作成するには  
  
1.  Perl 言語のコピーを取得します。  
  
2.  通常にある Perl スクリプト ConvertCTCToVSCT.pl のコピーを入手して、  *\<Visual Studio SDK インストール パス >* \VisualStudioIntegration\Tools\bin フォルダーです。  
  
3.  変換する .ctc ソース ファイルのコピーを取得します。  
  
4.  同じディレクトリにファイルを配置します。  
  
5.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンド プロンプト ウィンドウで、ディレクトリに移動します。  
  
6.  型  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     PkgCmd.ctc は .ctc ファイルの名前であり、PkgCmd.vsct は作成する .vsct ファイルの名前です。  
  
     新しい .vsct XML コマンド テーブル ソース ファイルが作成されます。 他の .vsct ファイルと同様に、Vsct.exe (VSCT コンパイラ) を使用してファイルをコンパイルできます。  
  
    > [!NOTE]
    >  XML コメントの書式を変更すると、.vsct ファイルの読みやすさを改善できます。  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>方法: 既存の .Cto ファイルから .Vsct ファイルを作成する  
  
既存のバイナリ .cto ファイルから XML ベースの .vsct ファイルを作成できます。 これを行うことで、新しいコマンド テーブル コンパイラ形式を活用できます。 このプロセスは、.ctc ファイルから .cto ファイルをコンパイルした場合でも機能します。 .vsct ファイルを編集して、別の .cto ファイルにコンパイルできます。  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>.cto ファイルから .vsct ファイルを作成するには  
  
1.  .Cto ファイルと、対応する .ctsym ファイルのコピーを取得します。  
  
2.  ファイルを Vsct.exe コンパイラと同じディレクトリに配置します。  
  
3.  Visual Studio コマンド プロンプトで、.cto ファイルと .ctsym ファイルが保存されているディレクトリに移動します。  
  
4.  型**vsct.exe** *ctofilename * * * .cto** * vsctfilename ***.vsct-s***symfilename ***.ctsym**です。  
  
     `ctofilename` .cto ファイルの名前を指定`vsctfilename`を作成する vsct ファイルの名前を指定し、 `symfilename` .ctsym ファイルの名前を指定します。  
  
     このプロセスによって、新しい .vsct XML コマンド テーブル コンパイラ ファイルが作成されます。 他の .vsct ファイルと同様に、vsct.exe (vsct コンパイラ) を使用して、ファイルを編集およびコンパイルできます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .Vsct ファイルをプロジェクトに追加するだけでは発生しませんしてコンパイルします。 ビルド プロセスでは、それを組み込む必要があります。  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>プロジェクトのコンパイルに .vsct ファイルを追加するには  
  
1.  エディターでは、プロジェクト ファイルを開きます。 場合は、プロジェクトが読み込まれると、まずアンロードする必要があります。  
  
2.  追加、 [ItemGroup 要素](../../msbuild/itemgroup-element-msbuild.md)を格納している、VSCTCompile 要素では、次の例で示すようにします。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 要素は常に設定する必要があります`Menus.ctmenu`です。  
  
3.  プロジェクトに .resx ファイルが含まれている場合は、次の例で示すように MergeWithCTO 要素を含む EmbeddedResource 要素を追加します。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     このマークアップは、埋め込みリソースを含む、ItemGroup 要素内移動する必要があります。  
  
4.  パッケージ ファイルを開いて、名前が付けられて*ProjectName*Package.cs または*ProjectName*Package.vb、エディターでします。  
  
5.  次の例で示すように、パッケージのクラスに ProvideMenuResource 属性を追加します。  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     最初のパラメーター値は、プロジェクト ファイルで定義されている ResourceName 属性の値に一致する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [作成します。Vsct ファイル](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)