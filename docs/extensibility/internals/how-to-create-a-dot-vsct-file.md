---
title: '方法: 作成します。Vsct ファイル |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b7c050022f129369962c572cbb5a60a27cca547
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979687"
---
# <a name="how-to-create-a-vsct-file"></a>方法: .Vsct ファイルを作成します。  
  
XML ベースの Visual Studio コマンド テーブル構成を作成するいくつかの方法があります (*.vsct*) ファイル。  
  
- 新しい VSPackage を作成することができます、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パッケージ テンプレート。  
  
- XML ベースのコマンド テーブル構成コンパイラを使用する*Vsct.exe*、既存のファイルを生成する *.ctc*ファイル。  
  
- 使用することができます*Vsct.exe*を生成する、 *.vsct*既存のファイル *.cto*ファイル。  
  
- 新しい手動で作成してできます *.vsct*ファイル。  
  
  この記事では、新たに手動で作成する方法をについて説明します *.vsct*ファイル。  
  
### <a name="to-manually-create-a-new-vsct-file"></a>新しい .vsct ファイルを手動で作成するには  
  
1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動します。  
  
2. **ファイル**メニューで、**新規**、 をクリックし、**ファイル**します。  
  
3. **テンプレート**ウィンドウで、をクリックして**XML ファイル**順にクリックします**オープン**します。  
  
4. **ビュー**  メニューのをクリックして**プロパティ**XML ファイルのプロパティを表示します。  
  
5. **プロパティ**ウィンドウで、をクリックして、**参照**のボタンでは、**スキーマ**プロパティ。  
  
6. XSD スキーマの一覧で選択、 *vsct.xsd*スキーマ。 一覧にいない場合、クリックして**追加**しローカル ドライブ上のファイルを検索します。 クリックして**OK**は終了するとき。  
  
7. XML ファイルで次のように入力します。 *< CommandTable*押します**タブ**します。」と入力してタグを閉じる *>* します。  
  
    この操作により、基本的な作成 *.vsct*ファイル。  
  
8. 従い、追加する XML ファイルの要素を入力、 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)します。 詳細については、次を参照してください[.vsct ファイルの作成。](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>方法: 既存の .ctc ファイルから .vsct ファイルを作成します。  
  
XML ベースを作成する *.vsct*コマンドの既存のテーブルからのファイル *.ctc*ソース ファイル。 これにより、新しい XML ベースの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] コマンド テーブル (VSCT) コンパイラ形式を利用できます。  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>.ctc ファイルから .vsct ファイルを作成するには  
  
1. Perl 言語のコピーを取得します。  
  
2. Perl スクリプトのコピーを入手*ConvertCTCToVSCT.pl*、一般にある、  *\<Visual Studio SDK インストール パス > \VisualStudioIntegration\Tools\bin*フォルダー。  
  
3. コピーを取得、 *.ctc*に変換するソース ファイル。  
  
4. 同じディレクトリにファイルを配置します。  
  
5. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンド プロンプト ウィンドウで、ディレクトリに移動します。  
  
6. 型  
  
   ```  
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
   ```  
  
    場所*PkgCmd.ctc*の名前を指定します、 *.ctc*ファイルと*PkgCmd.vsct*の名前を指定します、 *.vsct*ファイルを作成します。  
  
    この操作は、新しい作成 *.vsct* XML コマンド テーブル ソース ファイル。 使用して、ファイルをコンパイルする*Vsct.exe*、するとき、VSCT コンパイラはその他の *.vsct*ファイル。  
  
   > [!NOTE]
   >  読みやすさを向上させることができます、 *.vsct* XML コメントのフォーマット ファイル。  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>方法: 既存の .cto ファイルから .vsct ファイルを作成します。  
  
XML ベースを作成する *.vsct*既存のバイナリからファイル *.cto*ファイル。 これを行うことで、新しいコマンド テーブル コンパイラ形式を活用できます。 このプロセスはいて、 *.cto*からコンパイルされたファイル、 *.ctc*ファイル。 編集およびコンパイルしたことができます、 *.vsct*ファイルを別の .cto ファイルにします。  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>.cto ファイルから .vsct ファイルを作成するには  
  
1.  コピーを取得、 *.cto*ファイルとそれに対応する *.ctsym*ファイル。  
  
2.  同じディレクトリにファイルを配置、 *vsct.exe*コンパイラ。  
  
3.  Visual Studio のコマンド プロンプトでを含むディレクトリに移動、 *.cto*と *.ctsym*ファイル。  
  
4.  型  

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     場所\<ctofilename\>の名前を指定します、 *.cto*ファイル、 \<vsctfilename\>の名前を指定します、 *.vsct*ファイルを作成して\<symfilename\>の名前を指定します、 *.ctsym*ファイル。  
  
     このプロセスを作成する新しい *.vsct* XML コマンド テーブル コンパイラ ファイル。 編集して使用して、ファイルをコンパイル*vsct.exe*、するとき、vsct コンパイラはその他の *.vsct*ファイル。  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 追加するだけで、 *.vsct*ファイルをプロジェクトがコンパイルされません。 ビルド プロセスでは、それを組み込む必要があります。  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>プロジェクトのコンパイルに .vsct ファイルを追加するには  
  
1.  エディターで、プロジェクト ファイルを開きます。 プロジェクトが読み込まれている場合最初にアンロードする必要があります。  
  
2.  追加、 [ItemGroup 要素](../../msbuild/itemgroup-element-msbuild.md)を格納している、`VSCTCompile`要素は、次の例に示すようにします。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     `ResourceName`要素は常に設定する必要があります`Menus.ctmenu`します。  
  
3.  プロジェクトが含まれている場合、 *.resx*ファイルを追加、`EmbeddedResource`要素を含む、`MergeWithCTO`要素は、次の例に示すように。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     このマークアップは内で移動する必要があります、`ItemGroup`埋め込みリソースを含む要素。  
  
4.  という名前は、通常、パッケージ ファイルを開く *\<ProjectName\>Package.cs*または *\<ProjectName\>Package.vb*エディターでします。  
  
5.  追加、`ProvideMenuResource`の次の例に示すように、パッケージのクラスに属性します。  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     最初のパラメーター値の値に一致する必要があります、`ResourceName`プロジェクト ファイルで定義されている属性。  
  
## <a name="see-also"></a>関連項目  
 [.Vsct ファイルの作成者](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio コマンド テーブル (.vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)