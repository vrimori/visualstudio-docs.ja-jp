---
title: 'チュートリアル: Windows フォームでの単純な WCF サービスの作成'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e2c9d0bd58adcd0a0595c061fa4dfaa81f629601
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174248"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>チュートリアル: Windows フォームにおける単純な WCF サービスを作成します。

このチュートリアルは、単純な [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] サービスを作成し、テストして、Windows フォーム アプリケーションからアクセスする方法を例示しています。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>サービスを作成します。

### <a name="to-create-a-wcf-service"></a>WCF サービスを作成するには

1.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#** ノードをクリックします**WCF**、その後に**WCFサービス ライブラリ**します。 をクリックして**OK**プロジェクトを開きます。

     ![WCF サービス ライブラリ プロジェクト](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  これにより、テストしてアクセスすることが可能な機能するサービスが作成されます。 次の 2 つの手順は、別のデータ型を使用するように既定の方法を変更する方法を示しています。 実際のアプリケーションで、独自の関数をサービスに追加することもできます。

3.  ![IService1 ファイル](../data-tools/media/wcf2.png)

     **ソリューション エクスプ ローラー**、ダブルクリック**IService1.vb**または**IService1.cs**し、次の行を探します。

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     種類を変更、`value`文字列へのパラメーター。

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     上記のコードで、`<OperationContract()>` または `[OperationContract]` 属性に注意してください。 これらの属性は、サービスによって公開されている任意のメソッドに必要です。

4.  ![Service1 ファイル](../data-tools/media/wcf3.png)

     **ソリューション エクスプ ローラー**、ダブルクリック**Service1.vb**または**Service1.cs**し、次の行を探します。

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     種類を変更、`value`文字列へのパラメーター。

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>サービスをテストします。

### <a name="to-test-a-wcf-service"></a>WCF サービスをテストするには

1.  キーを押して**F5**サービスを実行します。 A **WCF テスト クライアント**フォームが表示され、サービスを読み込みます。

2.  **WCF テスト クライアント**フォームで、ダブルクリックして、 **GetData()** メソッド  **IService1**します。 **GetData**タブが表示されます。

     ![GetData&#40; &#41;メソッド](../data-tools/media/wcf4.png)

3.  **要求**ボックスで、選択、**値**フィールドと種類`Hello`します。

     ![[値] フィールド](../data-tools/media/wcf5.png)

4.  をクリックして、 **Invoke**ボタンをクリックします。 場合、**セキュリティ警告** ダイアログ ボックスが表示されたら、をクリックして**OK**します。 結果が表示されます、**応答**ボックス。

     ![[応答] ボックスに結果が表示される](../data-tools/media/wcf6.png)

5.  **ファイル** メニューのをクリックして**終了**テスト フォームを閉じます。

## <a name="access-the-service"></a>サービスへのアクセスします。

### <a name="to-reference-a-wcf-service"></a>WCF サービスを参照するには

1.  **ファイル**メニューで、**追加** をクリックし、**新しいプロジェクト**します。

2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#** ノードの  **Windows**、し、 **Windows フォーム アプリケーション**します。 をクリックして**OK**プロジェクトを開きます。

     ![Windows フォーム アプリケーション プロジェクト](../data-tools/media/wcf7.png)

3.  右クリック**WindowsApplication1**クリック**サービス参照の追加**します。 **サービス参照の追加** ダイアログ ボックスが表示されます。

4.  **サービス参照の追加**ダイアログ ボックスで、をクリックして**Discover**します。

     ![[サービス参照の追加] ダイアログ ボックス](../data-tools/media/wcf8.png)

     **Service1**で表示されます、**サービス**ウィンドウ。

5.  をクリックして**OK**サービス参照を追加します。

### <a name="to-build-a-client-application"></a>クライアント アプリケーションをビルドするには

1.  **ソリューション エクスプ ローラー**、ダブルクリックして**Form1.vb**または**Form1.cs**がまだ開いていない場合、Windows フォーム デザイナーを開きます。

2.  **ツールボックス**、ドラッグ、`TextBox`コントロール、`Label`コントロール、および`Button`コントロールをフォームにします。

     ![フォームへのコントロールの追加](../data-tools/media/wcf9.png)

3.  `Button` をダブルクリックし、`Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  **ソリューション エクスプ ローラー**を右クリックして**WindowsApplication1**クリック**スタートアップ プロジェクトとして設定**。

5.  キーを押して**F5**プロジェクトを実行します。 いくつかのテキストを入力し、ボタンをクリックします。 ラベルが表示されます"入力した:"と入力したテキストを表示します。

     ![結果を表示するフォーム](../data-tools/media/wcf10.png)

## <a name="see-also"></a>関連項目

- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)