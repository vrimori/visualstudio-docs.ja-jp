---
title: '方法: データベース内のデータへの接続 |Microsoft Docs'
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
- databases, connecting to
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e75de3c81270449da6fe6bb504b476b912f51583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273807"
---
# <a name="how-to-connect-to-data-in-a-database"></a>方法 : データベース内のデータに接続する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio を使用して、アプリケーションをデータベースに接続できます。 データ接続を作成すると、Visual Studio により、アプリケーションでデータベース内のデータと対話するために使用できるデータ モデルが生成されます。 データ モデルのオブジェクトに表示される、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)します。 項目をドラッグしてデータ バインド コントロールを作成し、**データ ソース ウィンドウ**デザイン サーフェイスにします。 詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。  
  
 ここでは、データベースに接続する方法と、次の種類のデータ モデルを作成する方法について説明します。  
  
-   データセット  
  
-   Entity Data Model (EDM)  
  
> [!NOTE]
>  また、Visual Studio を使用して、データベースから LINQ to SQL クラスを作成することもできます。 ただし、LINQ to SQL クラスは表示されませんで、**データ ソース**ウィンドウ、およびデータ バインド コントロールを作成するため、デザイナーに直接ドラッグすることはできません。 データベースから LINQ to SQL クラスを作成する詳細については、次を参照してください。[方法: LINQ to SQL クラスのテーブルとビュー (O/r デザイナー) にマップに作成](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)です。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> データベースへの接続とデータセットの作成  
 データベースに基づくデータセットを作成すると、Visual Studio により、データのプログラミング可能なビューを表す一連のクラスが作成されます。 メイン クラスを呼び出す、*型指定された dataset*します。 型指定されたデータセットは、データベースのテーブルを表すデータ テーブル オブジェクトを含みます。 型指定されたデータセットの詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)します。  
  
 データセットを作成したら、[データ ソース] ウィンドウから WPF デザイナーまたは Windows フォーム デザイナーにデータセット オブジェクトをドラッグすることにより、データ バインディング WPF コントロールまたはデータ バインディング Windows フォーム コントロールを作成できます。  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>アプリケーションをデータベースに接続してデータセットを作成するには  
  
1.  Visual Studio で既存のプロジェクトを開くか、新しいプロジェクトを作成します。  
  
2.  **[データ]** メニューの **[新しいデータ ソースの追加]** をクリックします。  
  
     **データ ソース構成ウィザード**が開きます。  
  
3.  **データ ソースの種類を選択**] ページで、[**データベース**、順にクリックします**次**します。  
  
4.  **データベース モデルの選択**] ページで、[**データセット**、順にクリックします**次**します。  
  
5.  **データ接続の選択** ページで利用可能な接続の一覧からデータ接続を選択してクリックして**次**します。  
  
     目的のデータ接続が使用できない場合は、次の手順に従って、新しい接続を作成[新しいデータベース接続を作成する](#CreatingDataConnection)します。  
  
6.  **アプリケーション構成ファイルへの接続文字列を保存** ページで、必要に応じてオフ、**接続を保存、** 場合は、コンパイルに直接接続文字列を保存する チェック ボックスアプリケーション。 既定では、接続がアプリケーション構成ファイルに保存されます。 詳細については、次を参照してください。[方法: 接続文字列の編集の保存および](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md)します。  
  
7.  **データベース オブジェクトの選択**ページで、アプリケーションで使用するデータベース オブジェクトを選択します。 既定値で置き換えることもある**データセット名**します。  
  
8.  **[完了]** をクリックします。 作成したデータセットで提供されて、**データソース**ウィンドウ。  
  
    > [!NOTE]
    >  場合、**データ ソース**ウィンドウが開いていない、] をクリックして **[データ ソースの**で、**データ**メニュー、ウィンドウを開きます。  
  
9. 項目をドラッグすることができます、**データ ソース**WPF デザイナー、Windows フォーム デザイナーにウィンドウまたは[Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282)データ バインド コントロールを作成します。 詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。  
  
##  <a name="edm"></a> データベースに接続して、エンティティ データ モデルの作成  
 データベースに基づく Entity Data Model を作成すると、Visual Studio により、データのプログラミング可能なビューを表す一連のクラスが作成されます。 Entity Data Model および ADO.NET Entity Framework の詳細については、次を参照してください。 [Entity Framework の概要](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)します。  
  
 Entity Data Model を作成したら、[データ ソース] ウィンドウから WPF デザイナーにエンティティ オブジェクトをドラッグすることにより、データ バインディング WPF コントロールを作成できます。  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>アプリケーションをデータベースに接続して Entity Data Model を作成するには  
  
1.  Visual Studio で既存のプロジェクトを開くか、新しいプロジェクトを作成します。  
  
2.  手順に従って、 **Entity Data Model ウィザード**データベースに接続し、モデルのコンテンツを指定します。 詳細については、次を参照してください。[方法: 新しい .edmx ファイルを作成する](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)します。  
  
3.  完了した後、 **Entity Data Model ウィザード**データ オブジェクトで使用できるようになりましたし、Entity Data Model デザイナーで作成した Entity Data Model を開き、**データソース**ウィンドウ。  
  
    > [!NOTE]
    >  場合、**データ ソース**ウィンドウが開いていない、] をクリックして **[データ ソースの**で、**データ**メニュー、ウィンドウを開きます。  
  
4.  項目をドラッグできるようになりました WPF デザイナーが開いている場合、**データソース**Entity Data Model にバインドされているコントロールを作成するデザイナーにウィンドウ。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)します。  
  
     項目をドラッグすることはできません、Windows フォーム デザイナーが開いている場合、**データソース**をデザイナーにします。 Entity Data Model にバインドされたコントロールを作成するには、プロジェクトをビルドし、Entity Data Model に基づく新しいオブジェクト データ ソースを追加し、それらのオブジェクトをデザイナーにドラッグする必要があります。  
  
##  <a name="CreatingDataConnection"></a> 新しいデータベース接続の作成  
 使用すると、**データ ソース構成ウィザード**または**Entity Data Model ウィザード**、使用するデータベースへの接続を指定する必要があります。 データベースへの接続がまだない場合は、次の手順を実行して接続を作成します。  
  
 これらの手順では、既に開始している前提としています、**データ ソース構成ウィザード**または**Entity Data Model ウィザード**」の説明に従って[データベースに接続して、データセットの作成](#dataset)と[データベースに接続して、Entity Data Model を作成する](#edm)します。  
  
#### <a name="to-create-a-new-database-connection"></a>新しいデータベース接続を作成するには  
  
1.  **データ接続の選択**のページ、**データ ソース構成ウィザード**または**Entity Data Model ウィザード**、 をクリックして**の新しい接続**.  
  
     次のいずれかのアクションが実行されます。  
  
    -   Visual Studio で、データ接続を既に作成している場合、**接続の追加** ダイアログ ボックスが表示されます。  
  
    -   Visual Studio で作成した最初のデータ接続の場合は、**データ ソースの選択** ダイアログ ボックスが表示されます。 接続をクリックするデータベースの種類を選択**OK**を表示する、**接続の追加** ダイアログ ボックス。  
  
2.  **接続の追加** ダイアログ ボックスで、要求された情報を入力します。 **接続の追加** ダイアログ ボックスは、データ プロバイダーの種類ごとに異なります。  
  
    > [!NOTE]
    >  場合、選択した**データソース**で、**接続の追加** ダイアログ ボックスは、をクリックして接続するデータ ソースではない**変更**を開く、**変更データソース** ダイアログ ボックスし、別のデータ ソースを選択します。  
  
3.  **接続の追加**ダイアログ ボックスで、をクリックして**OK**します。  
  
     戻る、**データ接続の選択**のページ、**データ ソース構成ウィザード**または**Entity Data Model ウィザード**します。  
  
4.  **データ接続の選択** ページで、新しいデータ接続が選択されていることを確認してクリックして**次**します。  
  
5.  残りの手順を完了、**データ ソース構成ウィザード**または**Entity Data Model ウィザード**します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データ ソースへの接続](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)