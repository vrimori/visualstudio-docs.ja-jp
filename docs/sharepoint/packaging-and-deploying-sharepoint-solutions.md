---
title: "SharePoint ソリューションの配置のパッケージ化と |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e25d0829305f414712590296b6121d62583736a2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="packaging-and-deploying-sharepoint-solutions"></a>SharePoint ソリューションのパッケージ化と配置
  通常、ソリューション パッケージ (.wsp) ファイルを使用して、SharePoint サーバーに SharePoint ソリューションを展開します。 機能に、SharePoint プロジェクト項目を整理して、SharePoint フィーチャーを配置するパッケージを作成するには、Visual Studio を使用することができます。  
  
 ここでは、次の情報について説明します。  
  
-   [フィーチャーとパッケージの作成](#Creating)  
  
-   [機能およびツールのサポートをパッケージ化](#Tools)  
  
-   [SharePoint ソリューションの配置](#Deploying)  
  
-   [SharePoint ソリューション内のファイルを展開します。](#DeployingFiles)  
  
##  <a name="Creating"></a>フィーチャーとパッケージの作成  
 関連する SharePoint 要素をグループ化する Visual Studio を使用することができます、*機能*します。 たとえば、連絡先リスト定義の機能には、リスト インスタンスと、リスト定義があります。 配置用に 1 つの機能には、これら 2 つの要素を結合できます。 機能の詳細については、次を参照してください。[ビルディング ブロック: 機能](http://go.microsoft.com/fwlink/?LinkID=169183)します。  
  
 次に、SharePoint ソリューション パッケージ (.wsp) を 1 つのパッケージに複数の機能、サイト定義、アセンブリ、およびその他のファイルをバンドルするファイルを保存する、SharePoint によって、ファイル サーバーを展開するために必要な形式で作成できます。 詳細については、次を参照してください。[ビルディング ブロック: ソリューション](http://go.microsoft.com/fwlink/?LinkID=169186)です。  
  
##  <a name="Tools"></a>機能およびツールのサポートをパッケージ化  
 Visual Studio での SharePoint 開発ツールを使用するにはすばやくファイル化する、SharePoint 機能とソリューションのパッケージを容易に展開します。 次のツールを使用すると、機能とソリューションのパッケージを構成します。  
  
-   デザイナーとパッケージ デザイナーを機能します。  
  
-   パッケージング エクスプ ローラー、ツール ウィンドウです。  
  
-   ソリューション エクスプ ローラー。  
  
### <a name="feature-designer-and-package-designer"></a>フィーチャー デザイナーとパッケージ デザイナー  
 機能を作成、スコープの設定、および依存関係として、フィーチャー デザイナーを使用して、その他の機能をマークできます。 デザイナーには、各機能を記述する最終的な XML ファイルも表示されます。 詳細については、次を参照してください。 [SharePoint 機能を作成する](../sharepoint/creating-sharepoint-features.md)です。  
  
 特定の Web サイトまたは Web サイトのグループを設定して、機能を適用、*スコープ*フィーチャー デザイナーでします。 個々 の Web サイトのフィーチャーがアクティブになる場合、機能は、その特定の Web サイトでのみ機能します。 サイト コレクションの機能がアクティブな場合、フィーチャー内の項目は、サイト全体のコレクションに適用されます。 詳細については、次を参照してください。[要素スコープ](http://go.microsoft.com/fwlink/?LinkID=169189)です。  
  
 機能は、その他の機能に依存する場合は、設定、*機能のアクティブ化依存関係*機能を使用できるようにする前に依存する機能をマークします。 機能のアクティブ化依存関係は、そのスコープに依存する機能が既にアクティブ化かどうかを確認します。 詳細については、次を参照してください。[アクティブ化依存関係とスコープ](http://go.microsoft.com/fwlink/?LinkID=169190)です。  
  
 パッケージ デザイナーでは、SharePoint 要素を 1 つのソリューション パッケージにグループ化し、配置時に、Web サーバーをリセットするかどうかを構成できます。 配置サーバーの種類を設定するには、使用、**プロパティ**ウィンドウです。 デザイナーには、パッケージの内容を記述する XML ファイルも生成されます。 詳細については、次を参照してください。 [SharePoint ソリューション パッケージの作成](../sharepoint/creating-sharepoint-solution-packages.md)です。  
  
 展開時に、SharePoint サーバーにソリューション ファイルをコピーする、インターネット インフォメーション サービス (IIS) サービスが停止しました。 Visual Studio で、パッケージ デザイナーを使用して、Web サーバーを再起動する必要があるかどうかを選択できます。 フロント エンド Web サーバーまたはアプリケーション サーバーに、ソリューションが展開されている場合を構成するを使用して、**プロパティ**ウィンドウです。 詳細については、次を参照してください。[ソリューション要素 (ソリューション)](http://go.microsoft.com/fwlink/?LinkID=169191)です。  
  
### <a name="packaging-explorer"></a>パッケージング エクスプ ローラー  
 フィーチャー デザイナーとパッケージ デザイナーを補完するためには、フィーチャーやパッケージに、SharePoint のファイルをグループ化するのにパッケージング エクスプ ローラーを使用できます。 さらに、パッケージ、フィーチャー、SharePoint プロジェクトの階層ビューを表示項目、およびファイルです。 パッケージング エクスプ ローラーでは、次のタスクを完了するのに使用できるツール ウィンドウを示します。  
  
-   SharePoint プロジェクト項目およびファイルを開きます。  
  
-   ドラッグし、1 つの機能から SharePoint プロジェクト項目をドロップします。  
  
-   ドラッグ アンド ドロップ SharePoint プロジェクト項目およびフィーチャー パッケージの 1 つにします。  
  
-   パッケージに新しい機能を追加します。  
  
-   フィーチャーまたはパッケージ デザイナーを開きます。  
  
-   フィーチャーとパッケージを検証します。  
  
 Visual Studio での SharePoint 開発ツールでは、ソリューション パッケージが正しく書式設定されていることを確認する検証規則があります。 さらに、ルールは、こと、.wsp というソリューション ファイルが正常に展開して、SharePoint サーバー上でアクティブ化を確認します。 機能の詳細については、XML スキーマは、次を参照してください。[機能スキーマ](http://go.microsoft.com/fwlink/?LinkID=169192)です。  
  
 SharePoint プロジェクト システムには、カスタムのフィーチャーとパッケージ検証規則を追加できます。 詳細については、次を参照してください。[する方法: カスタム機能の作成と SharePoint ソリューションのパッケージ検証規則](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)です。  
  
 パッケージング エクスプ ローラーの詳細については、次を参照してください。[する方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージング エクスプ ローラーを使用して](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)です。  
  
### <a name="solution-explorer"></a>ソリューション エクスプローラー  
 ソリューション エクスプ ローラーを使用して、移動し、SharePoint プロジェクトのファイルを開くことができます。 ソリューション エクスプ ローラーでコンテキスト メニューを使用して、フィーチャー イベント レシーバーのフィーチャーに追加し、フィーチャーのリソース。 さらに、機能と展開のパッケージを構成するには、フィーチャー デザイナーとパッケージ デザイナーを開くことができます。  
  
##  <a name="Deploying"></a>SharePoint ソリューションの配置  
 機能と Visual Studio でパッケージをカスタマイズした後は、SharePoint サーバーを展開する .wsp ファイルを作成することができます。 デバッグし、テスト、開発用コンピューター上の SharePoint サーバーでのみ .wsp を Visual Studio を使用することができます。 リモート SharePoint サーバーに、SharePoint ソリューションを配置する方法の詳細については、次を参照してください。[ソリューションを展開する](http://go.microsoft.com/fwlink/?LinkID=169194)です。  
  
 開発用コンピューターに展開の手順をカスタマイズすることもできます。 詳細については、次を参照してください。[を展開する、発行、および SharePoint ソリューション パッケージのアップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)です。  
  
##  <a name="DeployingFiles"></a>SharePoint ソリューション内のファイルを展開します。  
 通常は、SharePoint ソリューションを SharePoint プロジェクト項目を追加するときに必要なすべてのファイルが含まれています。 コンパイル済みの (コード ファイル) を使用可能なファイル、ソリューションの出力アセンブリに組み込まれます。 ただし、.xml、.txt、またはリソース ファイル、たとえば、非コンパイル可能なファイルを SharePoint プロジェクトに追加する必要がありますもします。 これらのファイルは、ソリューションに自動的にパッケージ化されません。 パッケージ化されることを確認するには、いずれかのファイルを追加、マップされたフォルダーまたは SharePoint プロジェクト項目。  
  
 マップされたフォルダーに追加されたファイルは、ソリューションを配置するときに自動的に SharePoint ハイブにコピーされます。 SharePoint プロジェクト項目に追加されたファイルで指定されている場所に配置されます、**配置場所**ファイルごとに、部分的に設定されているプロパティに基づいて、**展開の種類**プロパティです。 既定では、**展開の種類**プロパティの値が**NoDeployment**ファイルがソリューションで展開されていないことを意味します。 ファイルを含め、パッケージのプロパティに他の値を設定する必要があります。  
  
 たとえば、.xml ファイルを SharePoint プロジェクトを追加するには、これらのアクションのいずれかを実行します。  
  
-   SharePoint「レイアウト」のマップされたフォルダーをプロジェクトに追加します。 これで作成されます**ソリューション エクスプ ローラー**という名前のフォルダー**レイアウト**プロジェクト用のサブフォルダーを含むです。 新しいサブフォルダーに、.xml ファイルを追加します。 既定では、SharePoint のファイル システムにファイルの配置.\TEMPLATE\LAYOUTS\\*フォルダー名*\\です。 マップされたフォルダーを追加する方法については、次を参照してください。[する方法: 追加し、マップされたフォルダーを削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)です。  
  
-   SharePoint プロジェクト項目のフォルダーに .xml ファイルを追加し、変更、**展開の種類**から .xml ファイルのプロパティ**NoDeployment**別の設定がなどに**RootFile**または**ElementFile**です。 適切な**展開の種類**の設定、ファイルとプロジェクトに依存します。 詳細については、**展開の種類**プロパティの設定を参照してください[SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)です。  
  
 追加したファイルが適用される場合、ソリューション内の特定のプロジェクトへ、空の SharePoint プロジェクトをソリューションに追加でき、追加のファイルを追加できます。 特に、コンテンツ データベースに、SharePoint にファイルを展開するための別の方法としては、プロジェクトにモジュールを追加し、モジュールにファイルを追加するです。 詳細については、次を参照してください。[ソリューション内のインクルード ファイルを使用してモジュール](../sharepoint/using-modules-to-include-files-in-the-solution.md)です。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  