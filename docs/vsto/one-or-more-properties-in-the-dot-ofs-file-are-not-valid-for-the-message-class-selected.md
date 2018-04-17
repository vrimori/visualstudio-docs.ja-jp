---
title: .Ofs ファイルの 1 つ以上のプロパティは、選択されたメッセージ クラスに対して無効な |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac9f5ab05ba6ed858946b5f665d850eea51c230
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs ファイルの 1 つ以上のプロパティが、選択されたメッセージ クラスに対して有効ではありません
  このエラーは、Outlook でデザインしたフォーム領域をインポートする場合に、フォーム領域の 1 つ以上のフィールドが、 **新しいフォーム領域** ウィザードの最後のページで選択するメッセージ クラスと互換性がないときに発生します。  
  
 たとえば、 **新しいフォーム領域** ウィザードの最後のページで **[仕事 (IPM.Task)]** を選択したとします。 フォーム領域に **[会社住所]** フィールドが含まれている場合、タスクには会社住所がないため、このエラーが表示されます。 つまり、 **[会社住所]** フィールドは、IPM.Task メッセージ クラスとの互換性がないということです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   **新しいフォーム領域** ウィザードの最後のページで、フォーム領域のフィールドと互換性のあるメッセージ クラスを選択します。  
  
-   **新しいフォーム領域** ウィザードの最後のページで選択するメッセージ クラスと互換性のないフィールドは、Outlook のフォーム デザイナーで削除します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Outlook でデザインしたフォーム領域のインポート](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  