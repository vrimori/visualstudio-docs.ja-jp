---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、構成 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: BAE62C27-CA7A-4466-8738-3DB880221CE1
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 4e1cf47420cafda2552cdbb625d6d41626c32971
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="configure-easy-tables-in-azure"></a>Azure で簡易テーブルを構成する

簡易テーブルは [Azure Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/) の機能であり、この機能を利用すると、Azure Portal GUI で直接、SQL テーブルを設定し、管理できます。 Azure Mobile Apps はさまざまな機能に対応していますが、ここでは、Unity プロジェクトで Azure Mobile App バックエンドに格納されているデータを読み取り/書き込みする機能に限定して説明します。

## <a name="create-a-new-azure-mobile-app"></a>新しい Azure Mobile App を作成する

[Azure Portal](https://ms.portal.azure.com) にログインします。 Azure サブスクリプションをお持ちでない場合、[無料試用版](https://azure.microsoft.com/en-us/free/)か [Visual Studio Dev Essentials](https://www.visualstudio.com/dev-essentials/) に付属のクレジットをご利用ください。このチュートリアルの実行に十分な機能が提供されます。

**ポータル内で一回次の操作を行います。**

1. **[新規]、[Web + モバイル]、[モバイル アプリ]、[作成]** の順に選択します。

  ![新しいモバイル アプリを作成する](media/vstu_azure-configure-easy-tables-image1.png)

2. 新しいモバイル アプリを次のように構成します。

  * **[アプリ名]**。 この名前によって、Azure Mobile App バックエンドに接続するための URL が構築されます。 一意の名前を選択する必要があります。一意であることは緑のチェックマークで示されます。

  * **[サブスクリプション]**。 新しいモバイル アプリが請求に利用するサブスクリプションを選択します。

  * **[リソース グループ]**。 リソース グループを利用すると、関連するリソースの管理が楽になります。 Azure では既定で、新しいアプリと同じ名前で新しいリソース グループが作成されます。 このチュートリアルでは、初期設定で問題ありません。

  *  **[App Service プラン/場所]**。 サービス プランにより、新しいモバイル アプリをホストするために Azure が使用するリソースの処理能力、場所、コストが指示されます。 Azure では既定で、一部が初期設定のままで新しいサービス プランが作成されます。 これはチュートリアルであるため、最も簡単な選択を行います。 このメニューを利用し、新しいサービス プランの価格レベルや地域をカスタマイズできます。 さらに、デプロイ後、サービス プランの設定を変更できます。

  ![新しいモバイル アプリを作成する](media/vstu_azure-configure-easy-tables-image2.png)

3. **[作成]** を選択します。新しいリソースがデプロイされるまで数分待ちます。 デプロイが完了したら、Azure Portal に通知が表示されます。

## <a name="add-a-new-data-connection"></a>新しいデータ接続を追加する

4. デプロイが完了したら、**[すべてのリソース]** ボタンをクリックし、新しく作成したモバイル アプリを選択します。

  ![新しいモバイル アプリを選択する](media/vstu_azure-configure-easy-tables-image3.png)

5. 新しく開いたブレードの左にあるメニューで下にスクロールし、**[モバイル]** という見出しの下にある **[簡易テーブル]** ボタンをクリックします。

  ![簡易テーブルを選択する](media/vstu_azure-configure-easy-tables-image4.png)

6. [簡易テーブル] ブレードの一番上に表示される青色の **[簡易テーブル/簡易 API を構成する必要があります]** という通知をクリックします。

  ![簡易テーブルの構成通知をクリックする](media/vstu_azure-configure-easy-tables-image5.png)

7. **[You need a database to use Easy Tables.Click here to create one]\(簡易テーブルを使用するにはデータベースが必要です。ここをクリックして作成してください。\)** という通知をクリックします。

  ![データベース作成通知をクリックする](media/vstu_azure-configure-easy-tables-image6.png)

8. [データ接続] ブレードで、**[追加]** ボタンをクリックします。

  ![[追加] ボタンをクリックする](media/vstu_azure-configure-easy-tables-image7.png)

9. [データ接続の追加] ブレードで、**[SQL Database]** を選択します。

  ![SQL Database を選択する](media/vstu_azure-configure-easy-tables-image8.png)

10. 新しい SQL Database と SQL Server を構成するためのブレードが開きます。

  * **[名前]**。 データベースの名前を入力します。

  * **[対象サーバー]**。 **[対象サーバー]** をクリックし、[新しいサーバー] ブレードを開きます。

      * **[サーバー名]**。 サーバーの名前を入力します。

      * **[サーバー管理者ログイン] と [パスワード]**。 サーバー管理者とユーザー名とパスワードを作成します。

      * **[場所]**。 サーバーの近くにある場所を選択します。

      * **[Azure サービスにサーバーへのアクセスを許可する]** チェックボックスが選択されていることを確認します。

      * **[選択]** をクリックし、サーバーの構成を完了します。

    * **[価格レベル]**。 このチュートリアルでは、初期設定のままにします。 これは後で変更できます。

    * **[照合順序]**。 初期設定のままにします。

    * **[選択]** をクリックし、データベースの構成を完了します。

    ![SQL Server と SQL Database を構成する](media/vstu_azure-configure-easy-tables-image9.png)

11. [データ接続の追加] ブレードに戻り、**[接続文字列]** をクリックします。 [接続文字列] ブレードが表示されたら、初期設定のままで **[OK]** をクリックします。

  ![接続文字列をクリックする](media/vstu_azure-configure-easy-tables-image9.1.png)

12. [データ接続の追加] ブレードに戻ると、"MS_TableConnectionString" というテキストが斜体ではなくなっています。 **[OK]** をクリックします。新しいデータ接続が作成されるまで数分待ちます。 プロセスが完了すると通知が届きます。

  ![[OK] をクリックします。](media/vstu_azure-configure-easy-tables-image9.2.png)

## <a name="complete-the-easy-table-initialization"></a>簡易テーブルの初期化を完了する

13. 新しいデータ接続が作成されたら、**[すべてのリソース]** ボタンをクリックし、再度モバイル アプリに戻ります。 簡易テーブル構成通知を更新するために、この手順の実行は重要です。

14. 下にスクロールして **[簡易テーブル]** を選択し、もう一度青色の **[簡易テーブル/簡易 API を構成する必要があります]** 通知を選択します。

  ![簡易テーブル通知をクリックする](media/vstu_azure-configure-easy-tables-image5.png)

15. ブレードが表示されると、今度は **[1]** という見出しの下に "データ接続が既に存在します" と表示されるはずです。 見出し **[2]** の下で、**[これにより、すべてのサイト コンテンツが上書きされることを確認しました。]** チェックボックスを選択します。 **[アプリの初期化]** をクリックし、初期化プロセスが完了するまで数分待ちます。 プロセスが完了すると、新しい通知が表示されます。

  ![[アプリの初期化] をクリックする](media/vstu_azure-configure-easy-tables-image10.png)

## <a name="next-step"></a>次のステップ

* [簡易テーブルを作成する](visual-studio-tools-for-unity-azure-setup.md)
