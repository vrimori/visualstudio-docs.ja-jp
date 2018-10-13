---
title: '方法: ワークフロー デザイナーで検索を使用して |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6ff90f9e7916b598a1bf921f6de1e752afdb8b4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272543"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>ワークフロー デザイナーで検索を使用する方法
より大規模で複雑なワーク フローの作成を容易にするために、ワークフロー デザイナー内で検索を使用して、キーワードで項目を検索できます。 デザイナーでは、置換はサポートされないことに注意してください。 検索では、デザイナーで次の項目が検索されます。  
  
## <a name="quick-find"></a>クイック検索  
 クイック検索はデザイナー内で次の項目を検索します。  
  
-   <xref:System.Activities.Activity> オブジェクト、<xref:System.Activities.Statements.FlowNode> オブジェクト、<xref:System.Activities.Statements.State> オブジェクト、遷移、およびその他のカスタム フロー制御項目のプロパティ。  
  
-   変数  
  
-   引数  
  
-   式  
  
#### <a name="using-quick-find"></a>クイック検索の使用  
  
1.  ワークフロー デザイナーを開いた状態で、キーを押します**Ctrl + F**、または選択**編集**、**検索し、置換**、**クイック検索**します。  
  
2.  検索用語を入力してください、**検索**テキスト ボックス をクリック**次を検索**します。  
  
3.  検索用語が現在のワークフローで検索されます。 アクティビティの表示名がデザイナーで見つかったことを示すスクリーンショットを次に示します。  
  
     ![検索結果をワークフロー デザイナーで](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>フォルダーを指定して検索する  
 [フォルダーを指定して検索] を使用すると、XAML ファイルなどのワークフロー ファイル内で文字列が検索されます。  
  
#### <a name="using-find-in-files"></a>フォルダーを指定して検索の使用  
  
1.  Visual Studio で、キーを押して**Ctrl + Shift + F**、または選択**編集**、**検索し、置換**、**ファイル内の検索**  
  
2.  検索項目を入力してください、**検索**テキスト ボックス をクリック**すべて検索**  
  
3.  検索結果が表示されます、 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]**の検索結果**ビュー。 結果の項目をダブルクリックすると、ワークフロー デザイナーで一致する項目を含むアクティビティに移動します。