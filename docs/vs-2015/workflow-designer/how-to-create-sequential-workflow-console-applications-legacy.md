---
title: '方法: シーケンシャル ワークフロー コンソール アプリケーション (レガシ) を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0882a39dfae5639fcfc72adc7ccd976f4d93e30a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539430"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>方法: シーケンシャル ワークフロー コンソール アプリケーションを作成する (レガシ)
[!INCLUDE[wfd1](../includes/wfd1-md.md)] が備えている従来の [!INCLUDE[vs2010](../includes/vs2010-md.md)]を使用してシーケンシャル ワークフロー コンソール アプリケーション プロジェクトを作成するには、次の手順を実行します。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用します。  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>シーケンシャル ワークフロー コンソール アプリケーションを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  いずれかを選択、 **.NET Framework 3.0**オプションまたは **.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**従来のデザイナーにアクセスするウィンドウ。  
  
    > [!NOTE]
    >  既定のオプションに[!INCLUDE[vs2010](../includes/vs2010-md.md)]は **.NET Framework 4**します。 このオプションは、[!INCLUDE[wf](../includes/wf-md.md)] を対象とする [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] アプリケーションを作成する場合に使用され、従来のデザイナーは使用しません。  
  
4.  **プロジェクトの種類**ウィンドウ、Visual c# プロジェクトまたは Visual Basic プロジェクト (**他の言語**)、し、**ワークフロー**します。  
  
5.  **テンプレート**ペインで、**シーケンシャル ワークフロー コンソール アプリケーション**します。  
  
6.  **名前**ボックスに、簡単に特定できるように、プロジェクトのわかりやすい名前を入力します。  
  
7.  **場所**ボックスに、プロジェクトを保存またはをクリックするディレクトリを入力**参照**それに移動します。  
  
     Windows フォーム デザイナが開き、作成済みプロジェクトの Form1 が表示されます。  
  
8.  **[OK]** をクリックします。  
  
     ワークフロー デザイナが開き、作成済みシーケンシャル ワークフローのワークフロー デザイン サーフェイスが表示されます。  
  
9. アクティビティをドラッグして、**ツールボックス**でデザイン画面に、**アクティビティをドロップ**領域を指定します。  
  
## <a name="see-also"></a>関連項目  
 [従来のワークフロー プロジェクトを作成します。](../workflow-designer/creating-legacy-workflow-projects.md)   
 [ワークフローの開発](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)