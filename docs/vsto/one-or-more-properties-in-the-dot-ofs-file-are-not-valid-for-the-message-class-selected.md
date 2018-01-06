---
title: ".Ofs ファイルの 1 つ以上のプロパティは、選択されたメッセージ クラスに対して無効な |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ca816a635abf929f2bfa1614f4560f434adbfd45
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs ファイルの 1 つ以上のプロパティが、選択されたメッセージ クラスに対して有効ではありません
  このエラーは、Outlook でデザインしたフォーム領域をインポートする場合に、フォーム領域の 1 つ以上のフィールドが、 **新しいフォーム領域** ウィザードの最後のページで選択するメッセージ クラスと互換性がないときに発生します。  
  
 たとえば、 **新しいフォーム領域** ウィザードの最後のページで **[仕事 (IPM.Task)]** を選択したとします。 フォーム領域に **[会社住所]** フィールドが含まれている場合、タスクには会社住所がないため、このエラーが表示されます。 つまり、 **[会社住所]** フィールドは、IPM.Task メッセージ クラスとの互換性がないということです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   **新しいフォーム領域** ウィザードの最後のページで、フォーム領域のフィールドと互換性のあるメッセージ クラスを選択します。  
  
-   **新しいフォーム領域** ウィザードの最後のページで選択するメッセージ クラスと互換性のないフィールドは、Outlook のフォーム デザイナーで削除します。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: Outlook でデザインしたフォーム領域のインポート](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  