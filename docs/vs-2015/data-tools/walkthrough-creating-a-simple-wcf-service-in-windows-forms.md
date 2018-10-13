---
title: 'チュートリアル: Windows フォームでの単純な WCF サービスの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e73659c2d28cf97a8a7136ed8232cfbc5f0b77c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247209"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>チュートリアル: Windows フォームでの単純な WCF サービスの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
このチュートリアルは、単純な [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] サービスを作成し、テストして、Windows フォーム アプリケーションからアクセスする方法を例示しています。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>サービスの作成  
  
#### <a name="to-create-a-wcf-service"></a>WCF サービスを作成するには  
  
1.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#** ノードをクリックします**WCF**、その後に**WCFサービス ライブラリ**します。 をクリックして**OK**プロジェクトを開きます。  
  
     ![WCF サービス ライブラリ プロジェクト](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  これにより、テストしてアクセスすることが可能な機能するサービスが作成されます。 次の 2 つの手順は、別のデータ型を使用するように既定の方法を変更する方法を示しています。 実際のアプリケーションで、独自の関数をサービスに追加することもできます。  
  
3.  ![IService1 ファイル](../data-tools/media/wcf2.png "wcf2")  
  
     **ソリューション エクスプ ローラー**、IService1.vb または IService1.cs をダブルクリックし、次の行を探します。  
  
     [! コード csharp [WCFWalkthrough 4] (../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1 (2).cs 4)] [! コード vb [WCFWalkthrough 4] (../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1 (2).vb 4)]  
  
     `value` パラメーターの種類を `String` に変更します。  
  
     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
     上記のコードで、`<OperationContract()>` または `[OperationContract]` 属性に注意してください。 これらの属性は、サービスによって公開されている任意のメソッドに必要です。  
  
4.  ![Service1 ファイル](../data-tools/media/wcf3.png "wcf3")  
  
     **ソリューション エクスプ ローラー**、Service1.vb または Service1.cs をダブルクリックし、次の行を探します。  
  
     [! コード csharp [WCFWalkthrough 5] (../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1 (2).cs 5)] [! コード vb [WCFWalkthrough 5] (../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1 (2).vb 5)]  
  
     値パラメーターの種類を `String` に変更します。  
  
     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]  
  
## <a name="testing-the-service"></a>サービスのテスト  
  
#### <a name="to-test-a-wcf-service"></a>WCF サービスをテストするには  
  
1.  キーを押して**F5**サービスを実行します。 A **WCF テスト クライアント**フォームが表示され、サービスが読み込まれます。  
  
2.  **WCF テスト クライアント**フォームで、ダブルクリックして、 **GetData()** メソッド  **IService1**します。 **GetData**タブが表示されます。  
  
     ![GetData&#40; &#41;メソッド](../data-tools/media/wcf4.png "wcf4")  
  
3.  **要求**ボックスで、選択、**値**フィールドと種類`Hello`します。  
  
     ![[値] フィールド](../data-tools/media/wcf5.png "wcf5")  
  
4.  をクリックして、 **Invoke**ボタンをクリックします。 場合、**セキュリティ警告** ダイアログ ボックスが表示されたら、をクリックして**OK**します。 結果が表示されます、**応答**ボックス。  
  
     ![応答 ボックスに結果](../data-tools/media/wcf6.png "wcf6")  
  
5.  **ファイル** メニューのをクリックして**終了**テスト フォームを閉じます。  
  
## <a name="accessing-the-service"></a>サービスへのアクセス  
  
#### <a name="to-reference-a-wcf-service"></a>WCF サービスを参照するには  
  
1.  **ファイル**メニューで、**追加** をクリックし、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクト**] ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#** ノード**Windows**、し、[ **Windows フォーム アプリケーション**します。 をクリックして**OK**プロジェクトを開きます。  
  
     ![Windows フォーム アプリケーション プロジェクト](../data-tools/media/wcf7.png "wcf7")  
  
3.  右クリック**WindowsApplication1**クリック**サービス参照の追加**します。 **サービス参照の追加** ダイアログ ボックスが表示されます。  
  
4.  **サービス参照の追加**ダイアログ ボックスで、をクリックして**Discover**します。  
  
     ![サービス参照の追加 ダイアログ ボックス](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1**に表示される、**サービス**ウィンドウ。  
  
5.  をクリックして**OK**サービス参照を追加します。  
  
#### <a name="to-build-a-client-application"></a>クライアント アプリケーションをビルドするには  
  
1.  **ソリューション エクスプ ローラー**、ダブルクリックして**Form1.vb**または**Form1.cs**がまだ開いていない場合、Windows フォーム デザイナーを開きます。  
  
2.  **ツールボックス**、ドラッグ、`TextBox`コントロール、`Label`コントロール、および`Button`コントロールをフォームにします。  
  
     ![フォームにコントロールを追加する](../data-tools/media/wcf9.png "wcf9")  
  
3.  `Button` をダブルクリックし、`Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  **ソリューション エクスプ ローラー**を右クリックして**WindowsApplication1**クリック**スタートアップ プロジェクトとして設定**。  
  
5.  キーを押して**F5**プロジェクトを実行します。 いくつかのテキストを入力し、ボタンをクリックします。 ラベルに「You entered:」と入力したテキストが表示されます。  
  
     ![結果を表示するフォーム](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

