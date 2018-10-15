---
title: '方法: ワークフロー コンソール アプリケーションの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ad509e0e57f2c8996c13ffbe1d8f8890d2954dec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251668"
---
# <a name="how-to-create-a-workflow-console-application"></a>ワークフロー コンソール アプリケーションを作成する方法
[!INCLUDE[wf](../includes/wf-md.md)] を利用して、無人または有人のプロセスの実行のためのワークフローを作成できます。 [!INCLUDE[wfd1](../includes/wfd1-md.md)]は、このようなワークフローを作成するためのデザイン サーフェイスを備えています。 [!INCLUDE[wfd2](../includes/wfd2-md.md)]は、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 内からワークフローを作成する場合に使用でき、デザイナーを再ホストする他のアプリケーションに統合することもできます。  
  
 このトピックでは、[!INCLUDE[wfd2](../includes/wfd2-md.md)] の[!INCLUDE[vs2010](../includes/vs2010-md.md)]を使用して、コンソール アプリケーションのワークフローを作成する方法について説明します。  
  
### <a name="to-create-a-workflow-console-application"></a>ワークフロー コンソール アプリケーションを作成するには  
  
1.  [!INCLUDE[vs2010](../includes/vs2010-md.md)] を起動します。  
  
2.  **ファイル**メニューで、**新規**、し、**プロジェクト.**.  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **インストールされたテンプレート**ペインで、**ワークフロー**いずれかから、 **Visual c#** または**Visual Basic**に応じてグループの場合、言語の設定。  
  
4.  中央のペインで選択**ワークフロー コンソール アプリケーション**します。  
  
5.  **名前**ボックスに、簡単に特定できるように、プロジェクトのわかりやすい名前を入力します。  
  
6.  **場所**ボックスに、プロジェクトを保存またはをクリックするディレクトリを入力**参照**それに移動します。  
  
7.  **ソリューション**ボックスに、新しいソリューションの名前を入力します。 クリックして**OK**アプリケーションを作成します。  
  
    > [!NOTE]
    >  既存のソリューションのワークフロー コンソール アプリケーションを追加する場合は、そのソリューションを開きます[!INCLUDE[vs2010](../includes/vs2010-md.md)]でソリューションを右クリックして**ソリューション エクスプ ローラー**、選択および**追加**、し**新しいプロジェクト.** 開く、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。  
  
8.  プロジェクト テンプレートで XAML のワークフロー定義が作成され、コンソール アプリケーション定義がソース コードに記述されます。 [!INCLUDE[wfd2](../includes/wfd2-md.md)]で、作成したワークフロー用のキャンバスが開かれて表示されます。  
  
9. ワークフローを作成するアクティビティまたはからには、その他のワークフロー項目をドラッグ、**ツールボックス**ワークフロー デザイン サーフェイスにします。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)