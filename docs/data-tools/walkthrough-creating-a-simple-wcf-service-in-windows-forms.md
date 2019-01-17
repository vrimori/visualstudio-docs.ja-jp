---
title: 'チュートリアル: Windows フォームでのシンプルな WCF サービスの作成'
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
ms.workload:
- data-storage
ms.openlocfilehash: 466514f0bfd343dc985021a3a081739a91946f8e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882066"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>チュートリアル: Windows フォームでの単純な WCF サービスを作成します。

このチュートリアルは、単純な [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] サービスを作成し、テストして、Windows フォーム アプリケーションからアクセスする方法を例示しています。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>サービスを作成する

### <a name="to-create-a-wcf-service"></a>WCF サービスを作成するには

1.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2.  **[新しいプロジェクト]** ダイアログ ボックスで、**[Visual Basic]** または **[Visual C#]** ノードを展開し、**[WCF]** をクリックしてから **[WCF サービス ライブラリ]** をクリックします。 **[OK]** をクリックして、プロジェクトを開きます。

     ![WCF サービス ライブラリ プロジェクト](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  これにより、テストしてアクセスすることが可能な機能するサービスが作成されます。 次の 2 つの手順は、別のデータ型を使用するように既定の方法を変更する方法を示しています。 実際のアプリケーションで、独自の関数をサービスに追加することもできます。

3.  ![IService1 ファイル](../data-tools/media/wcf2.png)

     **ソリューション エクスプローラー**で、**IService1.vb** または **IService1.cs** をダブルクリックし、次の行を探します。

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     種類を変更、`value`文字列へのパラメーター。

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     上記のコードで、`<OperationContract()>` または `[OperationContract]` 属性に注意してください。 これらの属性は、サービスによって公開されている任意のメソッドに必要です。

4.  ![Service1 ファイル](../data-tools/media/wcf3.png)

     **ソリューション エクスプローラー**で、**Service1.vb** または **Service1.cs** をダブルクリックし、次の行を探します。

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     種類を変更、`value`文字列へのパラメーター。

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>サービスをテストします。

### <a name="to-test-a-wcf-service"></a>WCF サービスをテストするには

1.  **F5** キーを押してサービスを実行します。 A **WCF テスト クライアント**フォームが表示され、サービスを読み込みます。

2.  **[WCF のテスト用クライアント]** フォームで、**IService1** の下の **GetData()** メソッドをダブルクリックします。 **GetData**タブが表示されます。

     ![GetData&#40; &#41;メソッド](../data-tools/media/wcf4.png)

3.  **[要求]** ボックスで、**[値]** フィールドを選択して「`Hello`」と入力します。

     ![[値] フィールド](../data-tools/media/wcf5.png)

4.  **[起動]** ボタンをクリックします。 場合、**セキュリティ警告** ダイアログ ボックスが表示されたら、をクリックして**OK**します。 結果が表示されます、**応答**ボックス。

     ![[応答] ボックスに結果が表示される](../data-tools/media/wcf6.png)

5.  **[ファイル]** メニューの **[終了]** をクリックして、テスト フォームを閉じます。

## <a name="access-the-service"></a>サービスへのアクセスします。

### <a name="to-reference-a-wcf-service"></a>WCF サービスを参照するには

1.  **[ファイル]** メニューの **[追加]** をポイントし、**[新しいプロジェクト]** をクリックします。

2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#** ノードの  **Windows**、し、 **Windows フォーム アプリケーション**します。 **[OK]** をクリックして、プロジェクトを開きます。

     ![Windows フォーム アプリケーション プロジェクト](../data-tools/media/wcf7.png)

3.  **[WindowsApplication1]** を右クリックして **[サービス参照の追加]** をクリックします。 **サービス参照の追加** ダイアログ ボックスが表示されます。

4.  **[サービス参照の追加]** ダイアログ ボックスで **[探索]** をクリックします。

     ![[サービス参照の追加] ダイアログ ボックス](../data-tools/media/wcf8.png)

     **Service1**で表示されます、**サービス**ウィンドウ。

5.  **[OK]** をクリックしてサービス参照を追加します。

### <a name="to-build-a-client-application"></a>クライアント アプリケーションをビルドするには

1.  **ソリューション エクスプローラー**で、**[Form1.vb]** または **[Form1.cs]** をダブルクリックして、Windows フォーム デザイナーを (まだ開いていない場合に) 開きます。

2.  **ツールボックス**で、`TextBox` コントロール、`Label` コントロール、および `Button` コントロールをフォームにドラッグします。

     ![フォームへのコントロールの追加](../data-tools/media/wcf9.png)

3.  `Button` をダブルクリックし、`Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  **ソリューション エクスプローラー**で、**[WindowsApplication1]** を右クリックして **[スタートアップ プロジェクトに設定]** をクリックします。

5.  **F5** キーを押してプロジェクトを実行します。 いくつかのテキストを入力し、ボタンをクリックします。 ラベルが表示されます"入力した:"と入力したテキストを表示します。

     ![結果を表示するフォーム](../data-tools/media/wcf10.png)

## <a name="see-also"></a>関連項目

- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)