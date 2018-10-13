---
title: 'チュートリアル: ClickOnce 配置デザイナーを使用して API で必要に応じてサテライト アセンブリのダウンロード |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 5ca86e2ed1a05c8e325a99686281db3a7cf8f56e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306229"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>チュートリアル : デザイナーを使用し、ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

サテライト アセンブリを使用すると、複数のカルチャに対して Windows フォーム アプリケーションを構成できます。 *サテライト アセンブリ* とは、アプリケーションの既定のカルチャ以外のカルチャ用アプリケーション リソースを含むアセンブリのことです。  
  
 説明したよう[ClickOnce アプリケーションのローカライズ](../deployment/localizing-clickonce-applications.md)、同じ内に複数のカルチャ用の複数のサテライト アセンブリを含めることができます[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]展開します。 既定では、 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] により配置に含まれるすべてのサテライト アセンブリがクライアント コンピューターにダウンロードされます。ただし、多くの場合、1 つのクライアントに必要なサテライト アセンブリは 1 つだけです。  
  
 このチュートリアルでは、サテライト アセンブリをオプションとしてマークする方法、および現在のカルチャ設定にクライアント コンピューターが必要とするアセンブリのみをダウンロードする方法について説明します。  
  
> [!NOTE]
>  次のコード例は、テストを目的としているため、プログラム内でカルチャを `ja-JP` に設定しています。 このコードを運用環境用に調整する方法については、このトピックの「次の手順」セクションを参照してください。  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>サテライト アセンブリをオプションとしてマークするには  
  
1.  プロジェクトをビルドします。 これにより、ローカライズの対象としているすべてのカルチャについて、サテライト アセンブリが生成されます。  
  
2.  ソリューション エクスプ ローラーでプロジェクト名を右クリックし、をクリックして**プロパティ**します。  
  
3.  をクリックして、**発行**タブをクリックし、をクリックし、**アプリケーション ファイル**します。  
  
4.  選択、**ファイルをすべて表示**サテライト アセンブリを表示する チェック ボックス。 既定では、すべてのサテライト アセンブリが配置対象に含められ、このダイアログ ボックスに表示されます。  
  
     サテライト アセンブリは、フォームで、名前を持ちます*isoCode*\ApplicationName.resources.dll、場所*isoCode*は RFC 1766 形式の言語識別子です。  
  
5.  クリックして**新しい.** で、**ダウンロード グループ**各言語識別子のリスト。 ダウンロード グループ名の入力を求めるメッセージが表示されたら、言語識別子を入力します。 たとえば、日本語のサテライト アセンブリの場合は指定する、ダウンロード グループ名`ja-JP`します。  
  
6.  閉じる、**アプリケーション ファイル** ダイアログ ボックス。  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>必要に応じてサテライト アセンブリをダウンロードするには (C#)  
  
1.  Program.cs ファイルを開きます。 ソリューション エクスプ ローラーで、プロジェクトを選択します。 表示されない場合で、**プロジェクト**] メニューの [] をクリック **[すべてのファイル**します。  
  
2.  該当するサテライト アセンブリをダウンロードし、アプリケーションを起動するには、次のコードを使用します。  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs#1)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>必要に応じてサテライト アセンブリをダウンロードするには (Visual Basic)  
  
1.  **プロパティ**、アプリケーションのウィンドウでをクリックして、**アプリケーション**タブ。  
  
2.  タブ ページの下部には、次のようにクリックします。**アプリケーション イベントの表示**します。  
  
3.  ApplicationEvents.VB ファイルの先頭に、次の Imports ステートメントを追加します。  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#1)]  
  
4.  `MyApplication` クラスに次のコードを追加します。  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#2)]  
  
## <a name="next-steps"></a>次の手順  
 コード例を見ると、<xref:System.Threading.Thread.CurrentUICulture%2A> が特定の値に設定されています。しかし、運用環境では、クライアント コンピューターに適切な値が既定で設定されるため、この行は削除する必要があります。 たとえば、アプリケーションを日本語のクライアント コンピューターで実行する場合、既定では <xref:System.Threading.Thread.CurrentUICulture%2A> が `ja-JP` になります。 ここでは、アプリケーションの配置前にサテライト アセンブリをテストするという趣旨でプログラムから設定しています。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードします。](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [ClickOnce アプリケーションのローカライズ](../deployment/localizing-clickonce-applications.md)



