---
title: "方法 : Outlook にフォーム領域が表示されないようにする"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "キャンセル (フォーム領域表示を)"
  - "フォーム領域 [Visual Studio での Office 開発], キャンセル (表示を)"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 方法 : Outlook にフォーム領域が表示されないようにする
  Microsoft Office Outlook に特定のアイテムのフォーム領域を表示する必要がない場合があります。  たとえば、連絡先アイテムに勤務先の住所が含まれていない場合は、地図に勤務先の場所を表示するフォーム領域が表示されないように設定できます。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### Outlook にフォーム領域が表示されないようにするには  
  
1.  変更するフォーム領域のコード ファイルを開きます。  
  
2.  **\[フォーム領域ファクトリ\]** コード領域を展開します。  
  
3.  <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> クラスの <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> プロパティを **true** に設定する  `FormRegionInitializing` イベント ハンドラーにコードを追加します。  
  
 この例では、連絡先アイテムに住所が含まれていない場合、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> プロパティが **true** に設定され、フォーム領域が表示されません。  
  
## 使用例  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
## 参照  
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [チュートリアル : Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [チュートリアル : Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [チュートリアル : Outlook でデザインしたフォーム領域のインポート](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  