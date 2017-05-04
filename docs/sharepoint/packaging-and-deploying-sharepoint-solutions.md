---
title: "SharePoint ソリューションのパッケージ化と配置 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "配置 [Visual Studio での SharePoint 開発]"
  - "パッケージ化 [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, パッケージ化と配置"
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# SharePoint ソリューションのパッケージ化と配置
  通常、SharePoint ソリューションは、ソリューション パッケージ \(.wsp\) ファイルを使用して SharePoint サーバーに配置されます。  Visual Studio では、SharePoint プロジェクト項目をフィーチャーにまとめたり、SharePoint フィーチャーを配置するためのパッケージを作成したりすることができます。  
  
 ここでは、次の情報について説明します。  
  
-   [フィーチャーとパッケージの作成](#Creating)  
  
-   [フィーチャー ツールとパッケージ化ツールのサポート](#Tools)  
  
-   [SharePoint ソリューションの配置](#Deploying)  
  
-   [SharePoint ソリューションへのファイルの配置](#DeployingFiles)  
  
##  <a name="Creating"></a> フィーチャーとパッケージの作成  
 Visual Studio では、関連する SharePoint 要素を 1 つの*フィーチャー*にまとめることができます。  たとえば、連絡先リスト定義のフィーチャーには、リスト インスタンスとリスト定義が含まれます。  この 2 つの要素は、配置用に 1 つのフィーチャーにまとめることができます。  機能の詳細については、参照します [ビルド ブロック: フィーチャー](http://go.microsoft.com/fwlink/?LinkID=169183)。  
  
 さらに、SharePoint ソリューション パッケージ \(.wsp\) を作成して、複数のフィーチャー、サイト定義、アセンブリなどのファイルを 1 つのパッケージにバンドルすることにより、SharePoint がサーバーに配置するのに必要とする形式で一連のファイルをまとめることができます。  詳細については、参照します [ビルド ブロック: ソリューション](http://go.microsoft.com/fwlink/?LinkID=169186)。  
  
##  <a name="Tools"></a> フィーチャー ツールとパッケージ化ツールのサポート  
 Visual Studio では、SharePoint 開発ツールを使用して、一連の SharePoint ファイルを簡単に配置できるようにフィーチャーおよびソリューション パッケージにすばやくまとめることができます。  次のツールを使用してフィーチャーとソリューション パッケージを構成できます。  
  
-   フィーチャー デザイナーとパッケージ デザイナー。  
  
-   パッケージング エクスプローラー \(ツール ウィンドウ\)。  
  
-   ソリューション エクスプローラー。  
  
### フィーチャー デザイナーとパッケージ デザイナー  
 フィーチャー デザイナーを使用すると、フィーチャーを作成したり、スコープを設定したりできるだけではなく、他のフィーチャーを依存関係としてマークすることもできます。  このデザイナーでは、それぞれのフィーチャーを記述した最終的な XML ファイルも表示できます。  詳細については、「[SharePoint フィーチャーの作成](../sharepoint/creating-sharepoint-features.md)」を参照してください。  
  
 フィーチャー デザイナーでフィーチャーの*スコープ*を設定することによって、特定の Web サイト \(または Web サイトのグループ\) にフィーチャーを適用します。  個別の Web サイトに対してアクティブ化されたフィーチャーは、その特定の Web サイトでのみ使用できます。  サイト コレクションに対してフィーチャーがアクティブ化された場合、フィーチャー内の項目は、サイト コレクション全体に適用されます。  詳細については、参照します [要素のスコープ](http://go.microsoft.com/fwlink/?LinkID=169189)。  
  
 あるフィーチャーが他のフィーチャーに依存している場合、*フィーチャーのアクティブ化の依存関係*を設定することにより、依存元のフィーチャーをアクティブ化する前に依存先のフィーチャーをマークすることができます。  フィーチャーのアクティブ化の依存関係では、そのスコープで依存しているフィーチャーが既にアクティブ化されているかどうかをチェックします。  詳細については、参照します [アクティブ化の依存関係とスコープ](http://go.microsoft.com/fwlink/?LinkID=169190)。  
  
 パッケージ デザイナーでは、複数の SharePoint 要素を 1 つのソリューション パッケージにグループ化し、配置中に Web サーバーをリセットするかどうかを構成することができます。  配置用サーバーの種類を設定するには、**\[プロパティ\]** ウィンドウを使用します。  このデザイナーでは、パッケージの内容を記述した XML ファイルを生成することもできます。  詳細については、「[SharePoint ソリューション パッケージの作成](../sharepoint/creating-sharepoint-solution-packages.md)」を参照してください。  
  
 配置中は、ソリューション ファイルを SharePoint サーバーにコピーするためにインターネット インフォメーション サービス \(IIS: Internet Information Services\) のサービスが停止されます。  Web サーバーを再起動するかどうかは、Visual Studio でパッケージ デザイナーを使用して選択できます。  ソリューションをフロントエンド Web サーバーに配置するかアプリケーション サーバーに配置するかを構成するには、**\[プロパティ\]** ウィンドウを使用します。  詳細については、参照します [ソリューションの要素 \(ソリューション\)](http://go.microsoft.com/fwlink/?LinkID=169191)。  
  
### パッケージング エクスプローラー  
 パッケージング エクスプローラーは、SharePoint ファイルをフィーチャーおよびパッケージにグループ化する際の、フィーチャー デザイナーとパッケージ デザイナーの補助ツールとして使用できます。  それだけでなく、パッケージ、フィーチャー、SharePoint プロジェクト項目、およびファイルを階層表示することができます。  パッケージング エクスプローラーは、次のタスクの実行に使用できるツール ウィンドウです。  
  
-   SharePoint のプロジェクト項目およびファイルを開く。  
  
-   SharePoint プロジェクト項目をフィーチャー間でドラッグ アンド ドロップする。  
  
-   SharePoint のプロジェクト項目およびフィーチャーをパッケージ間でドラッグ アンド ドロップする。  
  
-   新しいフィーチャーをパッケージに追加する。  
  
-   フィーチャー デザイナーまたはパッケージ デザイナーを開く。  
  
-   フィーチャーとパッケージを検証します。  
  
 Visual Studio の SharePoint 開発ツールには、ソリューション パッケージが正しい形式になっていることを確認するための検証規則があります。  さらに、この規則では .wsp ソリューション ファイルを SharePoint サーバーに配置し、アクティブ化できることを検証します。  フィーチャーの XML スキーマに関する詳細については、参照します [機能スキーマ](http://go.microsoft.com/fwlink/?LinkID=169192)。  
  
 SharePoint プロジェクト システムには、カスタムのフィーチャーとパッケージの検証規則を追加できます。  詳細については、「[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)」を参照してください。  
  
 パッケージング エクスプローラーの詳細については、「[方法: パッケージング エクスプローラーを使用してパッケージのフィーチャーおよび項目を追加および削除する](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)」を参照してください。  
  
### ソリューション エクスプローラー  
 SharePoint プロジェクトのファイルは、ソリューション エクスプローラーで参照して開くことができます。  ソリューション エクスプローラーのコンテキスト メニューを使用して、フィーチャー、フィーチャーのイベント レシーバー、およびフィーチャーのリソースを追加します。  さらに、フィーチャー デザイナーおよびパッケージ デザイナーを開いて、配置用のフィーチャーとパッケージを構成することもできます。  
  
##  <a name="Deploying"></a> SharePoint ソリューションの配置  
 Visual Studio でフィーチャーとパッケージをカスタマイズしたら、SharePoint サーバーに配置するための .wsp ファイルを作成できます。  Visual Studio では、開発コンピューター上の SharePoint サーバー上でのみ、.wsp のデバッグとテストができます。  この方法の詳細についてはリモートの SharePoint サーバーに SharePoint ソリューションを配置する参照します [ソリューションの配置](http://go.microsoft.com/fwlink/?LinkID=169194)。  
  
 開発コンピューターでの配置手順をカスタマイズすることもできます。  詳細については、「[SharePoint ソリューションのパッケージの配置、発行、アップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)」を参照してください。  
  
##  <a name="DeployingFiles"></a> SharePoint ソリューションへのファイルの配置  
 通常は、SharePoint プロジェクト項目を SharePoint ソリューションに追加すると、必要なファイルがすべて含められます。  コンパイルできるファイル \(コード ファイル\) は、ソリューションの出力アセンブリに組み込まれます。  ただし、コンパイルできないファイル \(.xml、.txt、リソース ファイルなど\) を SharePoint プロジェクトに追加しなければならない場合があります。  これらのファイルは、ソリューションに自動的にパッケージされません。  これらのファイルを確実にパッケージするには、マップされたフォルダーまたは SharePoint プロジェクト項目にファイルを追加します。  
  
 マップされたフォルダーに追加されたファイルは、ソリューションが配置されるときに自動的に SharePoint ハイブにコピーされます。  SharePoint プロジェクト項目に追加されたファイルは、各ファイルの **\[配置場所\]** プロパティに指定された場所に配置されます。この場所は、部分的に **\[配置タイプ\]** プロパティに基づいて設定されます。  既定では、**\[配置タイプ\]** プロパティの値は **NoDeployment** です。これは、ファイルがソリューションと共に配置されないことを意味します。  ファイルをパッケージに含めるには、このプロパティに別の値を設定する必要があります。  
  
 たとえば、.xml ファイルを SharePoint プロジェクトに追加するには、次のいずれかを実行します。  
  
-   SharePoint のマップされたフォルダー "Layouts" をプロジェクトに追加します。  これにより、**ソリューション エクスプローラー**の中に、プロジェクトのサブフォルダーを持つ **Layouts** という名前のフォルダーが作成されます。  .xml ファイルを新しいサブフォルダーに追加します。  既定では、ファイルは、ファイルが配置されます。\\TEMPLATE\\LAYOUTS\\の*Folder Name*の\\。  マップされたフォルダーの追加方法については、「[方法: マップされたフォルダーを追加および削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)」を参照してください。  
  
-   .xml ファイルを SharePoint プロジェクト項目のフォルダーに追加し、.xml ファイルの **\[配置タイプ\]** プロパティを **NoDeployment** から別の設定 \(**RootFile** や **ElementFile** など\) に変更します。  **\[配置タイプ\]** の適切な設定は、ファイルとプロジェクトによって異なります。  **\[配置タイプ\]** プロパティの設定の詳細については、「[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)」を参照してください。  
  
 ソリューション内の特定のプロジェクトに適用しないファイルを追加する場合は、ソリューションに空の SharePoint プロジェクトを追加した後、その中にファイルを追加できます。  ファイルを SharePoint に \(特にコンテンツ データベースに\) 配置する別の方法として、モジュールをプロジェクトに追加した後、そのモジュールにファイルを追加することもできます。  詳細については、「[モジュールを使用してソリューションにファイルを追加する](../sharepoint/using-modules-to-include-files-in-the-solution.md)」を参照してください。  
  
## 参照  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  