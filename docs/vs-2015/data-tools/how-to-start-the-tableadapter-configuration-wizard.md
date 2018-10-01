---
title: '方法: TableAdapter 構成ウィザードを開始 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0cf7d3e5ace98ac73f97909b184ce04b86d4b9ee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538522"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>方法 :TableAdapter 構成ウィザードを開始する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**TableAdapter 構成ウィザード**を作成し、厳密に型指定されたデータセットに Tableadapter を編集します。 このウィザードでは、ウィザードに入力した SQL ステートメントまたはデータベース内の既存のストアド プロシージャに基づいて TableAdapter が作成されます。 このウィザードを使用すると、ウィザードに入力した SQL ステートメントに基づいて、データベース内に新しいストアド プロシージャを作成することもできます。  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>TableAdapter 構成ウィザードを開始して新しい TableAdapter を作成するには  
  
1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
    > [!NOTE]
    >  場合は、プロジェクト内のデータセットがないを参照してください。[作成し、データセットを構成](../data-tools/create-and-configure-datasets-in-visual-studio.md)します。  
  
2.  新しい TableAdapter を作成する場合は、ドラッグ、 **TableAdapter**オブジェクトから、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**.  
  
3.  **データ接続の選択**ページで、現在使用可能な接続の一覧からデータ接続を選択するか選択**新しい接続**新しい接続を作成します。  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>TableAdapter 構成ウィザードを開始して既存の TableAdapter を編集するには  
  
1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  TableAdapter を右クリックし、**データセット デザイナー**選択**構成**します。 ウィザードを使用、 **SQL ステートメントの生成**ページまたは**コマンドを既存のストアド プロシージャをバインド** ページで、TableAdapter の最初の構成方法に応じて、します。  
  
3.  ウィザードを完了します。  
  
## <a name="see-also"></a>関連項目  
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [方法: 並べ替えし、Windows フォーム BindingSource コンポーネントで ADO.NET データをフィルター処理](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [方法: Windows フォーム BindingSource コンポーネントを使用するルックアップ テーブルを作成](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)