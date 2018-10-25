---
title: データ アプリケーションの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4e5354d167dd6d3a1bef9beeb3dcaaaf24871bab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291318"
---
# <a name="creating-data-applications"></a>データ アプリケーションの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio には、データにアクセスするアプリケーションの作成に役立つ多くのデザイン時ツールが用意されています。 ここでは、データを操作するアプリケーションの作成に関する基本的なプロセスの概要について説明します。 この説明はデータ アプリケーションの作成に関連する多くの他のヘルプ トピックにリンクするための情報源となることを目的としており、詳細説明の多くは省略しています。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でデータにアクセスするアプリケーションを開発するにしたがって、さまざまな要件が発生します。 場合によっては、データをフォームに表示するだけで十分です。 また、他のアプリケーションまたはプロセスと情報を共有できるしくみが必要な場合もあります。  
  
 データに対する操作の種類に関係なく、理解しておく必要のある一定の基本的な概念があります。 多くの場合、データ処理に関する一部の詳細事項については知る必要はありません (たとえば、データベースをプログラムで作成する必要はありません)。しかし、基本的なデータ概念や、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で利用できるデータ ツール (ウィザードとデザイナー) について理解しておくと非常に役立ちます。  
  
 一般的なデータ アプリケーションは、次の図に示すようなプロセスの大部分を利用します。  
  
 ![データ サイクル グラフィック](../data-tools/media/datacyclegraphicinfo.gif "datacyclegraphicinfo")  
データ サイクル  
  
 アプリケーションを作成するときは、実行する必要のあるタスクについて検討する必要があります。 次の各セクションは、利用できる [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ツールとオブジェクトを見つけるのに役立ちます。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] には、前の図に示されている複数のプロセスを簡略化するためのウィザードが用意されています。 たとえば、実行している、**データ ソース構成ウィザード**データに接続し、データを受信する型指定されたデータセットを作成して、アプリケーションにデータを読み込むに必要な情報を使用してアプリケーションを提供します。  
  
 簡単に確認方法[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]データ アプリケーションの開発を参照してください[チュートリアル: 単純なデータ アプリケーションを作成する](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3)します。  
  
## <a name="connecting-to-data"></a>データへの接続  
 アプリケーションにデータを読み込んで変更内容をデータ ソースに返送するには、なんらかの双方向通信を確立する必要があります。 一般にこの双方向通信は、データ モデルのオブジェクトによって処理されます。  
  
 たとえば、`TableAdapter` はデータセットを使用するアプリケーションをデータベースに接続し、<xref:System.Data.Objects.ObjectContext> は Entity Framework のエンティティをデータベースに接続します。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] には、アプリケーションで使用できる接続の作成を支援するツールがいくつか用意されています。 アプリケーションをデータに接続する方法の詳細については、次を参照してください。 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)します。  
  
 データセットを使用して、アプリケーション データベース内のデータを接続する方法については、次を参照してください。[チュートリアル: データベース (Windows フォーム) 内のデータに接続する](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)します。  
  
## <a name="preparing-your-application-to-receive-data"></a>アプリケーションでデータを受け取るための準備  
 アプリケーションで非接続型データ モデルを使用する場合、データを操作するときにアプリケーションにデータを一時的に格納する必要があります。 Visual Studio には、アプリケーションがデータの一時的な格納に使用するオブジェクト (データセット、エンティティ、および [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] オブジェクト) を作成するのに役立つツールが用意されています。  
  
> [!NOTE]
>  一般に、非接続型データ モデルを使用するアプリケーションは、データベースに接続し、クエリを実行してアプリケーションにデータを読み込み、データベースから切断し、オフラインでデータを処理した後に再接続してデータベースを更新します。  
  
 アプリケーションで型指定されたデータセットを作成する方法の詳細については、次を参照してください。[データを受信するアプリケーションの準備](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)します。 N 層アプリケーションでデータセットの使用に関する詳細については、次を参照してください。[データセットと TableAdapters を別々 のプロジェクトに分割](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)します。  
  
 手順を完了すると、データセットを作成する方法については、[チュートリアル: データセット デザイナーでデータセットを作成する](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)します。  
  
 作成する方法について[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]オブジェクト、完了手順では、[チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成する](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)します。  
  
## <a name="fetching-data-into-your-application"></a>アプリケーションへのデータのフェッチ  
 アプリケーションで非接続型データ モデルを使用するかどうかにかかわらず、アプリケーションにデータをフェッチできる必要があります。 データベースに対してクエリまたはストアド プロシージャを実行することにより、アプリケーションにデータを読み込みます。 データセットにデータを格納するアプリケーションを使用してクエリやストアド プロシージャを実行する`TableAdapter`s、エンティティにデータを格納するアプリケーションを使用してクエリを実行する一方[LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d)またはエンティティを接続します。直接ストアド プロシージャ。 Tableadapter を使用してクエリ作成および編集の詳細については、次を参照してください。[方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)と[方法: TableAdapter クエリの編集](../data-tools/how-to-edit-tableadapter-queries.md)します。  
  
 データセットにデータの読み込みとクエリとストアド プロシージャを実行する方法の詳細については、次を参照してください。[アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)します。  
  
 データセットにデータを読み込む方法については、完了手順では、[チュートリアル: Windows フォーム上でデータを表示する](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)フォーム読み込みイベント ハンドラーでコードを確認します。  
  
 データを読み込む方法については[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]オブジェクト、完了手順では、[チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成する](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)します。  
  
 作成し、SQL クエリを実行する方法については、次を参照してください。[方法: を作成し、その行を返しますの SQL ステートメントを実行](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed)します。  
  
 ストアド プロシージャを実行する方法については、次を参照してください。[方法: ストアド プロシージャを実行するには、その行を返します](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d)します。  
  
## <a name="displaying-data-on-forms"></a>フォームでのデータの表示  
 アプリケーションにデータを読み込んだら、通常はそのデータをフォームに表示して、ユーザーが表示または変更できるようにします。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)、自動的にデータを表示するデータ バインド コントロールを作成するフォームに項目をドラッグできます。 データ バインドと、ユーザーへのデータ表示の詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。  
  
 ユーザーにデータを表示する方法については、次のチュートリアルの手順を完了します (から項目をドラッグするプロセスに特に注意してください、**データソース**ウィンドウ)。  
  
-   [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)します。  
  
-   [WCF Data Service への WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [チュートリアル: WCF データ サービスへの Silverlight コントロールのバインド](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>アプリケーションでのデータ編集  
 データがユーザーに表示されると、ユーザーは新しいレコードを追加したり、レコードの編集や削除を行ってそのデータを変更してから、データベースにデータを返送する場合があります。  
  
 データセットに読み込まれると、データを操作する方法の詳細については、次を参照してください。[アプリケーションでデータを編集](../data-tools/editing-data-in-your-application.md)します。  
  
## <a name="validating-data"></a>データの検証  
 データを変更する場合、通常は変更内容を検証してからデータセットに値を戻したりデータベースに書き込むことができるようにします。 *検証*これらの新しい値が、アプリケーションの要件を満たすことを確認するため、プロセスの名前を指定します。 値を変更するときにアプリケーションで値を検査するロジックを追加できます。 Visual Studio には、列および行の変更時にデータを検証するコードを追加するためのツールが用意されています。 詳細については、次を参照してください。[データ妥当性検査](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)します。  
  
 データの検証をアプリケーションに追加する方法については、次を参照してください。[チュートリアル: データセットに検証の追加](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7)します。  
  
 N 層アプリケーションに分離されたデータセットに検証を追加する方法については、次を参照してください。 [n 層データセットに検証を追加](../data-tools/add-validation-to-an-n-tier-dataset.md)します。  
  
## <a name="saving-data"></a>データの保存  
 アプリケーションで変更を行って変更内容を検証した後、通常は変更内容をデータベースに返送します。 データをデータセットに格納するアプリケーションは、通常 TableAdapterManager を使用してデータを保存します。 詳細については、次を参照してください。 [TableAdapterManager の概要](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)します。 Entity Framework アプリケーションを使用して、<xref:System.Data.Objects.ObjectContext.SaveChanges%2A>メソッド データを保存します。  
  
 更新されたデータをデータベースに送信する詳細については、次を参照してください。[データの保存](../data-tools/saving-data.md)します。  
  
 データセットからデータベースに更新されたデータを送信する方法については、完了手順では、[チュートリアル: 関連データ テーブル (階層更新) からのデータの保存](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b)します。  
  
## <a name="related-topics"></a>関連トピック  
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 データを操作するアプリケーションを作成する方法について説明しているトピックへのリンクを示します。  
  
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)  
 使用する方法に関するトピックへのリンクを提供します。[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]アプリケーション データを接続すると、アプリケーションのデータ ソースを作成します。  
  
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 アプリケーションでデータセットや Entity Data Model などのデータ モデルを操作する方法について説明しているトピックへのリンクを示します。  
  
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)  
 アプリケーションにデータを読み込む方法について説明しているトピックへのリンクを示します。  
  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Windows フォーム コントロール、WPF コントロール、および Silverlight コントロールをデータ ソースにバインドする方法について説明しているトピックへのリンクを示します。  
  
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)  
 アプリケーションでデータを変更する方法について説明しているトピックへのリンクを示します。  
  
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 データ変更に検証を加える方法について説明しているトピックへのリンクを示します。  
  
 [データの保存](../data-tools/saving-data.md)  
 更新したデータをアプリケーションからデータベースに送信する方法、またはそれらのデータを XML などの他の形式に保存する方法について説明しているトピックへのリンクを示します。  
  
 [Visual Studio でのデータ ソースを操作するためのツール](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 など、Visual Studio でのデータ ソースを操作するのに使用できるツールに関するトピックへのリンクを提供、**データソース**ウィンドウと ADO.NET Entity Data Model デザイナー。