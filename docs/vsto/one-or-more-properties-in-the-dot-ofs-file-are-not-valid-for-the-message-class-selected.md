---
title: .ofs ファイルの 1 つ以上のプロパティが、選択されたメッセージ クラスに対して有効ではありません
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
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692500"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs ファイルの 1 つ以上のプロパティが、選択されたメッセージ クラスに対して有効ではありません
  Outlook でデザインしたフォーム領域をインポートするときに、このエラーが表示されますが、フォーム領域上の 1 つ以上のフィールドがの最後のページで選択したメッセージ クラスと互換性がありません、**新しいフォーム領域**ウィザード。  

たとえば、 **新しいフォーム領域** ウィザードの最後のページで **[仕事 (IPM.Task)]** を選択したとします。 フォーム領域がある場合、**会社住所**フィールドでは、タスクは、会社の住所があるないために、このエラーを受信します。 したがって、**会社住所**フィールドと互換性がない、 `IPM.Task` message クラスです。  
  
 選択した可能性があります**タスク (IPM です。タスク)** の最後のページで、**新しいフォーム領域**ウィザード。 フォーム領域がある場合、**会社住所**フィールドでは、タスクは、会社の住所があるないために、このエラーを受信します。 したがって、**会社住所**フィールドと互換性がない、 `IPM.Task` message クラスです。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   **新しいフォーム領域** ウィザードの最後のページで、フォーム領域のフィールドと互換性のあるメッセージ クラスを選択します。  
  
-   Outlook でフォーム デザイナーでは、メッセージ クラスと互換性のないフィールドを削除します。 最後のページで選択しようとするフィールドを削除する、**新しいフォーム領域**ウィザード。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Outlook でデザインしたフォーム領域をインポートします。](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  