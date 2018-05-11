---
title: '方法: サービスのデータに接続する'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3975d7f0bcfc9b80c944c892cde52f2b625e0bbf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-connect-to-data-in-a-service"></a>方法: サービスのデータに接続する

アプリケーションを実行して、サービスから返されたデータを接続する、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を選択して**サービス**上、 **データソースの種類を選択して**ページ。

完了すると、ウィザードのサービス参照がプロジェクトに追加されですぐに使用できるは、[データ ソース ウィンドウ](add-new-data-sources.md)します。

> [!NOTE]
> 表示される項目、**データソース**ウィンドウは、サービスから返される情報に依存します。 一部のサービス可能性がありますのに十分な情報を提供していない、**データ ソース構成ウィザード**バインド可能なオブジェクトを作成します。 たとえば場合、サービスでは、型指定されていないデータセットを返します、し、項目も表示されません、**データ ソース ウィンドウ**ウィザードを完了するとします。 これは、型指定されていないデータセット提供しないので、スキーマ、ウィザードでは、データ ソースを作成するための十分な情報は必要がありません。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>アプリケーションをサービスに接続するには

1.  **[データ]** メニューの **[新しいデータ ソースの追加]** をクリックします。

2.  選択**サービス**上、**データ ソースの種類を選択** ページで、クリックして**次へ**です。

3.  使用して、またはをクリックする、サービスのアドレスを入力**Discover**を現在のソリューション内でサービスを検索し、をクリックして**移動**です。

4.  必要に応じて、新しい**Namespace**既定値の代わりに型指定することができます。

    > [!NOTE]
    > をクリックして**詳細**を開くには、[サービス参照の構成 ダイアログ ボックス](../data-tools/configure-service-reference-dialog-box.md)です。

5.  をクリックして**OK**サービス参照をプロジェクトに追加します。

6.  **[完了]** をクリックします。

     データ ソースを追加、**データソース**ウィンドウです。

## <a name="next-steps"></a>次の手順

機能をアプリケーションに追加する項目を選択、**データソース**ウィンドウし、バインドされたコントロールを作成するフォームにドラッグします。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)です。

## <a name="see-also"></a>関連項目

- [WCF Data Service への WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)