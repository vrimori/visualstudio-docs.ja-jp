---
title: 'チュートリアル: ClickOnce 配置デザイナーを使用して API で必要に応じてアセンブリをダウンロードする |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 827f524a5038c57283f33e519f3df972dbf72b26
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547659"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>チュートリアル : デザイナーを使用し、ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[チュートリアル: ClickOnce 配置 API を使用して、デザイナーで必要に応じてアセンブリをダウンロード](https://docs.microsoft.com/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)します。  
  
既定では、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションに含まれるすべてのアセンブリが、アプリケーションを初めて実行したときにダウンロードされます。 ただし、アプリケーションには少数のユーザーにしか使われない部分が含まれることがあります。 その場合は、そのような型を作成するときにだけアセンブリをダウンロードすることができます。 以下のチュートリアルでは、アプリケーション内の特定のアセンブリに "オプション" マークを付ける方法、および共通言語ランタイムでそのアセンブリが必要なときに <xref:System.Deployment.Application> 名前空間にあるクラスを使用してアセンブリをダウンロードする方法について説明します。  
  
> [!NOTE]
>  これを行うには、アプリケーションが完全な信頼で実行する必要があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Visual Studio でオンデマンド アセンブリを使用するプロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で新しい Windows フォーム プロジェクトを作成します。 **[ファイル]** メニューの **[追加]** をポイントし、 **[新しいプロジェクト]** をクリックします。 ダイアログ ボックスで **[クラス ライブラリ]** プロジェクトを選択し、名前を `ClickOnceLibrary`に設定します。  
  
    > [!NOTE]
    >  Visual Basic でプロジェクトのプロパティを変更し、このプロジェクトのルート名前空間を `Microsoft.Samples.ClickOnceOnDemand` または他の適切な名前空間にすることをお勧めします。 わかりやすくするため、このチュートリアルでは 2 つのプロジェクトを同じ名前空間にします。  
  
2.  `DynamicClass` という名前のプロパティを 1 つ持つ `Message`という名前のクラスを定義します。  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3.  **ソリューション エクスプローラー**で Windows フォーム プロジェクトを選択します。 <xref:System.Deployment.Application> アセンブリに対する参照および `ClickOnceLibrary` プロジェクトに対するプロジェクト参照を追加します。  
  
    > [!NOTE]
    >  Visual Basic でプロジェクトのプロパティを変更し、このプロジェクトのルート名前空間を `Microsoft.Samples.ClickOnceOnDemand` または他の適切な名前空間にすることをお勧めします。 わかりやすくするため、このチュートリアルでは 2 つのプロジェクトを同じ名前空間にします。  
  
4.  フォームを右クリックし、メニューの **[コードの表示]** をクリックして、次の参照をフォームに追加します。  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5.  このアセンブリをオンデマンドでダウンロードする次のコードを追加します。 このコードでは、 <xref:System.Collections.DictionaryBase.Dictionary%2A> ジェネリック クラスを使用してアセンブリのセットをグループ名にマップする方法を示します。 このチュートリアルではダウンロードするアセンブリが 1 つだけなので、グループに含まれるアセンブリは 1 つのみです。 実際のアプリケーションでは、アプリケーションの 1 つの機能に関連するすべてのアセンブリを同時にダウンロードすることがあります。 マッピング テーブルを使用すると、機能に属しているすべての DLL をダウンロード グループ名に関連付けることにより、これを簡単に実行できます。  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6.  **[表示]** メニューの **[ツールボックス]** をクリックします。 <xref:System.Windows.Forms.Button> ツールボックス **からフォームに** をドラッグします。 ボタンをダブルクリックして、 <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>アセンブリをオプションとしてマークする  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Visual Studio を使用して ClickOnce アプリケーションでアセンブリをオプションとしてマークするには  
  
1.  **ソリューション エクスプローラー** で Windows フォーム プロジェクトを右クリックし、 **[プロパティ]** をクリックします。 **[発行]** タブを選択します。  
  
2.  **[アプリケーション ファイル]** ボタンをクリックします。  
  
3.  ClickOnceLibrary.dll のリストを探します。 **[発行の状況]** ドロップダウン ボックスを **[含む]** に設定します。  
  
4.  **[グループ]** ドロップダウン ボックスを展開し、 **[新規]** を選択します。 新しいグループ名として「 `ClickOnceLibrary` 」と入力します。  
  
5.  」の説明に従って、アプリケーションの発行を続行[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)します。  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>マニフェストの生成および編集ツールを使用して ClickOnce アプリケーションでアセンブリをオプションとしてマークするには — グラフィカル クライアント (MageUI.exe)  
  
1.  作成、 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 」の説明に従ってマニフェスト[チュートリアル: ClickOnce アプリケーションを手動で配置](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。  
  
2.  MageUI.exe を終了する前に、配置のアプリケーション マニフェストを含むタブを選択し、そのタブで **[ファイル]** タブを選択します。  
  
3.  アプリケーション ファイルの一覧で ClickOnceLibrary.dll を探し、 **[ファイルの種類]** 列を **[なし]** に設定します。 **[グループ]** 列に「 `ClickOnceLibrary.dll`」と入力します。  
  
## <a name="testing-the-new-assembly"></a>新しいアセンブリをテストする  
  
#### <a name="to-test-your-on-demand-assembly"></a>オンデマンド アセンブリをテストするには  
  
1.  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] で配置されたアプリケーションを起動します。  
  
2.  メイン フォームが表示されたら、 <xref:System.Windows.Forms.Button>をクリックします。 メッセージ ボックスに "Hello, World!" と表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application.ApplicationDeployment>



