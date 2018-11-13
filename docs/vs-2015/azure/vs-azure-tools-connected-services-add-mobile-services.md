---
title: Visual studio 接続済みサービスを使用して、Mobile Services の追加 |Microsoft Docs
description: Visual Studio 接続されているサービスの追加 ダイアログ ボックスを使用して Mobile Services の追加します。
documentationcenter: na
author: ghogen
manager: douge
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 1679f8e20c4516ab64c4358229b4eec6ab5029ba
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002902"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Visual Studio 接続済みサービスを使用して Mobile Services を追加します。
Visual Studio 2015 では、Azure Mobile Services を使用してに接続できる、 **接続済みサービス**ダイアログ。 いずれかから接続できるC#クライアント アプリ、JavaScript アプリ、またはクロスプラット フォーム Cordova アプリです。 接続すると、作成しデータにアクセス、カスタム Api と、スケジュールされたジョブを作成したりプッシュ通知のサポートを追加します。  接続済みサービスの操作では、すべての適切な参照と接続コードを追加します。 さまざまな Azure AD などの人気 id スキームを使用した認証用の組み込みサポートを利用を行うことができ、Facebook、Twitter、Microsoft アカウント。

## <a name="supported-project-types"></a>サポートされているプロジェクトの種類
> [!NOTE]
> Visual Studio 2015 で、ユニバーサル Windows (Windows 10) プロジェクトに接続済みサービスの追加 ダイアログを使用して Azure Mobile Services を追加することはサポートされていません。 Azure Mobile Services を追加するには、プロジェクトの NuGet パッケージ マネージャーを使用して適切なパッケージをインストールします。
> 
> 

接続済みサービス ダイアログを使用すると、次の種類のプロジェクトで Azure Mobile Services に接続します。

* .NET Windows 8.1 ストア、Phone、ユニバーサル アプリ プロジェクト
* JavaScript Windows 8.1 ストア、Phone、ユニバーサル アプリ プロジェクト
* Apache Cordova の Visual Studio Tools を使用して作成されたプロジェクト

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>接続済みサービスの追加 ダイアログを使用して Azure Mobile Services に接続します。
1. Azure アカウントを持っていることを確認します。 サインアップすることができます、Azure アカウントを持っていない場合、[無料試用版](http://go.microsoft.com/fwlink/?LinkId=518146)します。
2. 開く、**接続済みサービスの追加** ダイアログ ボックス。
   
   * .NET アプリの場合は、Visual Studio でプロジェクトを開き、コンテキスト メニューを開き、**参照**ソリューション エクスプ ローラーでノードをクリックして**接続済みサービスの追加**
     
        ![Azure モバイル サービスに接続します。](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Apache Cordova アプリ プロジェクトでは、Visual Studio でプロジェクトを開き、ソリューション エクスプ ローラーでプロジェクト ノードのコンテキスト メニューを開き、および選択**接続済みサービス**します。
3. **接続済みサービスの追加** ダイアログ ボックスで、選択**Azure Mobile Services**、選択し、**構成**ボタンをクリックします。 これをまだ完了していない場合は、Azure にログインが求められるあります。
   
    ![Azure のモバイル サービスを追加します。](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. **Azure Mobile Services**  ダイアログ ボックスで、1 つがある場合は、既存のモバイル サービスを選択します。 新しい Azure モバイル サービスを作成する必要がある場合は、これを行うには次の手順に従います。 それ以外の場合は次の手順に進みます。
   
    新しいモバイル サービス アカウントを作成します。
   
   1. 選択、* * サービスの作成 * * ダイアログ ボックスの下部にあるリンクです。
       ![新しいモバイル接続サービスを追加します。](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. **モバイル サービスの作成**ダイアログ ボックスで、JavaScript バックエンド モバイル サービスまたは .NET バックエンド モバイル サービスからを選択できる、**ランタイム**ドロップダウン リスト。 
      
       ![モバイル サービスを作成します。](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)
      
       JavaScript バックエンド サービスとは、単純で強力です。 JavaScript バックエンド モバイル サービスを作成する場合は、サーバー側の JavaScript コードが、クラウドに格納されているが、サーバー エクスプ ローラーまたは Azure 管理ポータルを使用してサーバー スクリプトを編集することができます。 
      
       .NET バックエンド モバイル サービスでは、完全な機能と Web API と Entity Framework の柔軟性を提供します。 .NET バックエンド モバイル サービスを作成する場合、プロジェクトが自動的に作成し、ソリューションに追加します。 
   3. 選択、**リージョン**モバイル サービスでは、して、サーバーのユーザー名とパスワードを入力します。
   4. 必要なすべての情報を入力したら、選択、**作成**モバイル サービスを作成するボタンをクリックします。
   5. 新しいモバイル サービスは、サービスの一覧に表示する、 **Azure Mobile Services**  ダイアログ ボックス。 一覧で新しいモバイル サービスを選択し、選択、**追加**をプロジェクトにサービスを追加するボタンをクリックします。
5. 表示される作業の開始ページを確認し、プロジェクトがどのように変更されたかを確認します。 接続済みサービスを追加するたびに、ブラウザーで作業の開始ページが表示されます。 推奨される次の手順とコード例については、確認したりの変更点をプロジェクトに追加された参照と、コードと構成ファイルが変更された方法を表示するページに切り替えます。
6. ガイドとしてコード サンプルを使用して、開始、モバイル サービスにアクセスするコードを記述します。

## <a name="how-your-project-is-modified"></a>プロジェクトを変更する方法
Visual Studio でプロジェクトを変更する方法は、プロジェクトの種類によって異なります。 C#クライアント アプリを参照してください[内容 –C#プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=513119)します。 JavaScript クライアント アプリでは、次を参照してください。[内容 – JavaScript プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=513120)します。 Cordova アプリでは、次を参照してください。[内容 – Cordova プロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=513116)します。

## <a name="next-steps"></a>次の手順
質問してヘルプを表示します。 

* [MSDN フォーラム: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Microsoft Azure チームのブログで azure Mobile Services](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure の Mobile Services (azure.microsoft.com)](https://azure.microsoft.com/services/mobile-services/)
* [Azure Mobile Services のドキュメント (azure.microsoft.com)](https://azure.microsoft.com/documentation/services/mobile-services/)

