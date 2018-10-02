---
title: '方法: を作成します。Vsct ファイル |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79d2c0c059d9e257fc0239731fb013a56c6dd6a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547513"
---
# <a name="how-to-create-a-vsct-file"></a>方法: を作成します。Vsct ファイル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: を作成します。Vsct ファイル](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-create-a-dot-vsct-file)します。  
  
Visual Studio コマンド テーブルの XML ベースの構成 (.vsct) ファイルを作成するいくつかの方法はあります。  
  
-   新しい VSPackage を作成することができます、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]パッケージ テンプレート。  
  
-   XML ベースのコマンド テーブル構成コンパイラ Vsct.exe を使用すると、既存の .ctc ファイルからファイルを生成します。  
  
-   Vsct.exe を使用して、既存の .cto ファイルから .vsct ファイルを生成することができます。  
  
-   新しい .vsct ファイルを手動で作成することができます。  
  
 このトピックでは、新しい .vsct ファイルを手動で作成する方法について説明します。  
  
### <a name="to-manually-create-a-new-vsct-file"></a>新しい .vsct ファイルを手動で作成するには  
  
1.  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を起動します。  
  
2.  **ファイル**メニューで、**新規**、 をクリックし、**ファイル**します。  
  
3.  **テンプレート**ウィンドウで、をクリックして**XML ファイル**順にクリックします**オープン**します。  
  
4.  **ビュー**  メニューのをクリックして**プロパティ ウィンドウ**XML ファイルのプロパティを表示します。  
  
5.  **プロパティ**ウィンドウで、スキーマ プロパティの参照ボタン (…) ボタンをクリックします。  
  
6.  XSD スキーマの一覧で、vsct.xsd スキーマを選択します。 一覧にいない場合、クリックして**追加**しローカル ドライブ上のファイルを検索します。 クリックして**OK**は終了するとき。  
  
7.  XML ファイルで次のように入力します。`<CommandTable`し、TAB キーを押します。 」と入力してタグを閉じる`>`します。  
  
     これには、基本的な .vsct ファイルが作成されます。  
  
8.  従い、追加する XML ファイルの要素を入力、 [VSCT スキーマ](../../extensibility/vsct-xml-schema-reference.md)します。 詳細については、次を参照してください。[作成します。Vsct ファイル](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .Vsct ファイルをプロジェクトに追加することだけは発生しませんコンパイルすること。 ビルド プロセスでは、それを組み込む必要があります。  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>プロジェクトのコンパイルに .vsct ファイルを追加するには  
  
1.  エディターで、プロジェクト ファイルを開きます。 プロジェクトが読み込まれている場合最初にアンロードする必要があります。  
  
2.  追加、 [ItemGroup 要素](../../msbuild/itemgroup-element-msbuild.md)VSCTCompile 要素を含む次の例に示すようにします。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 要素は常に設定する必要があります`Menus.ctmenu`します。  
  
3.  プロジェクトに .resx ファイルが含まれている場合は、次の例に示すように、MergeWithCTO 要素を含む EmbeddedResource 要素を追加します。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     このマークアップは、埋め込みリソースを含む ItemGroup 要素内で移動する必要があります。  
  
4.  という名前は、通常、パッケージ ファイルを開く*ProjectName*Package.cs または*ProjectName*Package.vb、エディターでします。  
  
5.  次の例に示すように、パッケージのクラスに ProvideMenuResource 属性を追加します。  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     最初のパラメーター値は、プロジェクト ファイルで定義した ResourceName 属性の値に一致する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [作成します。Vsct ファイル](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [方法: を作成します。既存の Vsct ファイルです。Ctc ファイル](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [方法: を作成します。既存の Vsct ファイルです。Cto ファイル](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)

