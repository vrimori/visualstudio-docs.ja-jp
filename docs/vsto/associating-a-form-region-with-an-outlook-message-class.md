---
title: フォーム領域を Outlook メッセージ クラスに関連付ける
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e28653749b19c9f53bd8e43e245fd8dcb20aa31
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050263"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>フォーム領域を Outlook メッセージ クラスに関連付ける
  Microsoft Office Outlook アイテム フォーム領域を各項目のメッセージ クラスに関連付けることによって、フォーム領域を表示するを指定することができます。 たとえば、メール アイテムの下部にフォーム領域を追加する場合は、フォーム領域を関連付けることができます、 `IPM.Note` message クラス。  
  
 関連付けるメッセージ クラスを使用してフォーム領域には、メッセージのクラス名を指定、**新しい Outlook フォーム領域**ウィザードか、フォーム領域ファクトリ クラスに属性を適用します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understand-outlook-message-classes"></a>Outlook メッセージ クラスを理解します。  
 Outlook メッセージ クラスは、Outlook アイテムの種類を識別します。 次の表では、8 種類の標準項目とのメッセージ クラス名の一覧表示します。  
  
|Outlook アイテムの種類|メッセージ クラス名|  
|-----------------------|------------------------|  
|AppointmentItem|`IPM.Appointment`|  
|ContactItem|`IPM.Contact`|  
|配布リスト|`IPM.DistList`|  
|JournalItem|`IPM.Activity`|  
|MailItem|`IPM.Note`|  
|PostItem|`IPM.Post` または `IPM.Post.RSS`|  
|TaskItem|`IPM.Task`|  
  
 カスタム メッセージ クラスの名前を指定することもできます。 カスタム メッセージ クラスは、Outlook で定義したカスタムのフォームを識別します。  
  
> [!NOTE]  
>  置換およびすべて置換フォーム領域では、新しいカスタム メッセージ クラス名を指定できます。 既存のカスタム フォームのメッセージ クラス名を使用する必要はありません。 カスタム メッセージ クラスの名前は一意である必要があります。 名前が一意であることを確認する方法の 1 つは、次のような名前付け規則を使用する: \< *StandardMessageClassName*>.\<*会社*>.\<*MessageClassName*> (例: `IPM.Note.Contoso.MyMessageClass`)。  
  
## <a name="associate-a-form-region-with-an-outlook-message-class"></a>フォーム領域を Outlook メッセージ クラスに関連付ける  
 関連付けるメッセージ クラスのフォーム領域の 2 つの方法はあります。  
  
-   使用して、**新しい Outlook フォーム領域**ウィザード。  
  
-   クラスの属性を適用します。  
  
### <a name="use-the-new-outlook-form-region-wizard"></a>新しい Outlook フォーム領域ウィザードの使用  
 最後のページで、**新しい Outlook フォーム領域**ウィザードの標準のメッセージ クラスを選択し、フォーム領域に関連付けるカスタム メッセージ クラスの名前を入力することができます。  
  
 標準のメッセージ クラスは全体のフォームまたはフォームの既定のページを置換するフォーム領域が設計されている場合に使用できません。 フォームに新しいページを追加するか、フォームの下部に追加されるフォームに対してのみ、標準のメッセージ クラス名を指定できます。 詳細については、次を参照してください。[方法: フォーム領域を Outlook アドイン プロジェクトに追加](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)します。  
  
 1 つまたは複数のカスタム メッセージ クラスを含めるでその名前を入力、**カスタム メッセージ クラスは、このフォーム領域を表示するか。** ボックス。  
  
 入力した名前は、次のガイドラインに準拠する必要があります。  
  
- メッセージの完全修飾クラス名を使用して (例:"IPM します。Note.Contoso")。  
  
- セミコロンを使用して、複数のメッセージ クラス名を区切ります。  
  
- "IPM など、標準の Outlook メッセージ クラスが含まれていません。注"または"IPM します。Contact"です。 "IPM などのカスタム メッセージ クラスのみを含めます。Note.Contoso"。  
  
- 単独では、基本メッセージ クラスを指定しない (例:"IPM")。  
  
- 各メッセージ クラス名の 256 文字をを超えてはなりません。  
  
  **新しい Outlook フォーム領域**をクリックすると、ウィザードは、入力の形式を検証**完了**します。  
  
> [!NOTE]  
>  **新しい Outlook フォーム領域**ウィザードが提供するメッセージ クラス名は正確性や有効なことを確認していません。  
  
 ウィザードを完了すると、**新しい Outlook フォーム領域**ウィザードでは、指定されたメッセージ クラス名が含まれているフォーム領域クラスに属性が適用されます。 これらの属性を手動で適用することもできます。  
  
### <a name="apply-class-attributes"></a>クラスの属性を適用します。  
 完了した後、Outlook メッセージ クラスをフォーム領域を関連付けることができます、**新しい Outlook フォーム領域**ウィザード。 これを行うには、属性をフォーム領域ファクトリ クラスに適用します。  
  
 次の例では 2 つ<xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute>という名前のフォーム領域ファクトリ クラスに適用されている属性`myFormRegion`します。 最初の属性は、メール メッセージの形式の標準のメッセージ クラスを使用して、フォーム領域を関連付けます。 2 番目の属性は、という名前のカスタム メッセージ クラスを使用してフォーム領域を関連付けます`IPM.Task.Contoso`します。  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 属性は、次のガイドラインに準拠する必要があります。  
  
- カスタム メッセージ クラスに、メッセージの完全修飾クラス名を使用します (例:"IPM します。Note.Contoso")。  
  
- 単独では、基本メッセージ クラスを指定しない (例:"IPM")。  
  
- 各メッセージ クラス名の 256 文字をを超えてはなりません。  
  
- フォーム領域全体のフォームまたはフォームの既定のページを置き換える場合は、標準のメッセージ クラスの名前を含めないでください。 フォームに新しいページを追加するか、フォームの下部に追加されるフォームに対してのみ、標準のメッセージ クラス名を指定できます。 詳細については、次を参照してください。[方法: フォーム領域を Outlook アドイン プロジェクトに追加](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)します。  
  
  Visual Studio は、プロジェクトをビルドするときに、メッセージのクラス名の形式を検証します。  
  
> [!NOTE]  
>  Visual Studio では、指定したメッセージ クラス名は正確性や有効なことは検証しません。  
  
## <a name="see-also"></a>関連項目  
 [実行時にフォーム領域へのアクセスします。](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook フォーム領域を作成します。](../vsto/creating-outlook-form-regions.md)   
 [チュートリアル: Outlook フォーム領域をデザインします。](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Outlook フォーム領域を作成するためのガイドライン](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [フォームの名前とメッセージ クラスの概要](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)   
 [フォームとアイテムを連携させる方法](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)  
  
  