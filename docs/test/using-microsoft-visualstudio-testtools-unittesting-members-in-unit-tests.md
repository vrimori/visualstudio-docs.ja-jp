---
title: "単体テストでの Microsoft.VisualStudio.TestTools.UnitTesting のメンバーの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mlearned"
manager: "douge"
---
# 単体テストでの Microsoft.VisualStudio.TestTools.UnitTesting のメンバーの使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

単体テスト フレームワークは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] での単体テストをサポートします。  単体テストをコーディングする場合は、<xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework> 名前空間のクラスとメンバーを使用します。  単体テストを最初から作成する場合や、テストしているコードから生成された単体テストを調整する場合に、これらを使用できます。  
  
## 要素のグループ  
 単体テスト フレームワークの概要を明らかにするために、このセクションでは、UnitTesting 名前空間の要素を関連機能のグループに整理します。  
  
> [!NOTE]
>  名前に文字列 Attribute が含まれる属性要素は、文字列 Attribute が付いていても付いていなくても使用できます。  たとえば、次の 2 つのコード例は、同じように機能します。  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### データ ドリブン テストで使用する要素  
 データ ドリブン単体テストを設定するには、次の要素を使用します。  詳細については、「[方法: データ ドリブン単体テストを作成する](../test/how-to-create-a-data-driven-unit-test.md)」および「[チュートリアル : データ ソースを定義するための構成ファイルの使用](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)」を参照してください。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection>  
  
## 呼び出し順序を確立するために使用する属性  
 次のいずれかの属性で装飾されたコード要素は、指定した時点で呼び出されます。  詳細については、「[Anatomy of a Unit Test](http://msdn.microsoft.com/ja-jp/a03d1ee7-9999-4e7c-85df-7d9073976144)」を参照してください。  
  
### アセンブリ用  
 AssemblyInitialize はアセンブリがロードされた直後、AssemblyCleanup はアセンブリがアンロードされる直前に呼び出されます。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute>  
  
### クラス用  
 ClassInitialize はクラスがロードされた直後、ClassCleanup はクラスがアンロードされる直前に呼び出されます。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute>  
  
### テスト メソッド用  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute>  
  
## テスト クラスおよびメソッドの識別に使用する属性  
 各テスト クラスには TestClass 属性が必要です。また、各テスト メソッドには TestMethod 属性が必要です。  詳細については、「[Anatomy of a Unit Test](http://msdn.microsoft.com/ja-jp/a03d1ee7-9999-4e7c-85df-7d9073976144)」を参照してください。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute>  
  
## アサート クラスおよび関連する例外  
 単体テストでは、さまざまな Assert ステートメント、例外、および属性を使用することによって、特定のアプリケーション動作を検査できます。  詳細については、「[Assert クラスの使用](../test/using-the-assert-classes.md)」を参照してください。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute>  
  
## TestContext クラス  
 次の属性およびそれらの属性に割り当てられる値は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で、特定のテスト メソッドの \[プロパティ\] ウィンドウに表示されます。  これらの属性は、単体テストのコードからアクセスされることは目的としていません。  その代わりに、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の IDE、または [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] テスト エンジンが単体テストを使用または実行するときの方法に影響します。たとえば、これらの属性には、\[テスト マネージャー\] ウィンドウや \[テスト結果\] ウィンドウの列として表示されるものがあり、それらを使用してテストやテスト結果をグループ化したり並べ替えたりできます。  このような属性の 1 つに TestPropertyAttribute があります。この属性を使用して、任意のメタデータを単体テストに追加できます。  たとえば、単体テストを `[TestProperty("TestPass", "Accessibility")]` とマークして、このテストで扱うテスト パスの名前を格納するために使用できます。  また、`[TestProperty("TestKind", "Localization")]` を使用して、テストの種類のインジケーターを格納できます。  この属性を使用して作成するプロパティ、および割り当てるプロパティ値は、どちらも [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の \[プロパティ\] ウィンドウの **\[各テストで特有\]** という見出しの下に表示されます。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute>  
  
## テスト構成クラス  
  
-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection>  
  
## レポートの生成に使用する属性  
 このセクションの属性は、[!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] チーム プロジェクトのプロジェクト階層内のエンティティに、この属性が修飾するテスト メソッドを関連付けます。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute>  
  
## プライベート アクセサーと共に使用するクラス  
 「[Using Publicize to Create a Private Accessor](http://msdn.microsoft.com/ja-jp/2056c6a7-6672-42a7-8f53-fead33c56deb)」で説明されているように、プライベート メソッドの単体テストを生成できます。  生成するとプライベート アクセサー クラスが作成され、このクラスにより、PrivateObject クラスのオブジェクトがインスタンス化されます。  PrivateObject クラスは、プライベート アクセサー プロセスの一部としてリフレクションを使用するラッパー クラスです。  これは PrivateType クラスに似ていますが、PrivateType クラスは、プライベート インスタンス メソッドの呼び出しではなく、プライベート静的メソッドの呼び出しに使用されます。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType>  
  
## 参照  
 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>