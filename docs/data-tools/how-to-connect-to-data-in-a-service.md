---
title: '方法: サービスのデータに接続する'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0affe931e5b85d32acdc95fecaa50f3b7f2fe8f4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39175700"
---
# <a name="how-to-connect-to-data-in-a-service"></a>方法: データ サービスに接続するには

アプリケーションを実行して、サービスから返されたデータを接続する、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)選択**サービス**上、 **のデータソースの種類を選択**ページ。

ウィザードの完了したら、サービス参照をプロジェクトに追加されですぐに使用できるは、[データ ソース ウィンドウ](add-new-data-sources.md)します。

> [!NOTE]
> 表示される項目、**データソース**ウィンドウは、サービスが返す情報に依存します。 一部のサービスがのに十分な情報を提供していない、**データ ソース構成ウィザード**バインド可能なオブジェクトを作成します。 たとえば、サービスは、型指定されていないデータセットを返す場合項目表示されません、**データ ソース ウィンドウ**ウィザードを完了するとします。 これは、ウィザードには、データ ソースを作成するのに十分な情報がないため、型指定されていないデータセットがスキーマで提供されないためにです。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>アプリケーション サービスに接続するには

1.  **[データ]** メニューの **[新しいデータ ソースの追加]** をクリックします。

2.  選択**サービス**上、**データ ソースの種類を選択**] ページの [クリックして **[次へ]**。

3.  使用して、またはをクリックする、サービスのアドレスを入力**Discover**をクリックして、現在のソリューションでのサービスを探します**移動**します。

4.  必要に応じて、入力、新しい**Namespace**既定値の代わりにします。

    > [!NOTE]
    > をクリックして**詳細**を開く、[サービス参照の構成 ダイアログ ボックス](../data-tools/configure-service-reference-dialog-box.md)します。

5.  をクリックして**OK**をプロジェクトにサービス参照を追加します。

6.  **[完了]** をクリックします。

     データ ソースを追加、**データソース**ウィンドウ。

## <a name="next-steps"></a>次の手順

アプリケーションに機能を追加するには、内の項目を選択、**データソース**ウィンドウ バインドされたコントロールを作成するためのフォームにドラッグします。 詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。

## <a name="see-also"></a>関連項目

- [WCF Data Service への WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)