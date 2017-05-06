---
title: "フォーム領域の Outlook メッセージ クラスへの関連付け"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewFormRegionWizard.InvalidMessageClassName"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "フォーム領域 [Visual Studio での Office 開発], メッセージ クラス"
  - "FormRegionMessageClassAttribute"
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# フォーム領域の Outlook メッセージ クラスへの関連付け
  フォーム領域を各アイテムのメッセージ クラスに関連付けることにより、そのフォーム領域を表示する Microsoft Office Outlook アイテムを指定できます。  たとえば、フォーム領域をメール アイテムの下部に表示する場合は、そのフォーム領域を IPM.Note メッセージ クラスに関連付けることができます。  
  
 フォーム領域をメッセージ クラスに関連付けるには、**新しい Outlook フォーム領域**ウィザードでメッセージ クラス名を指定するか、フォーム領域ファクトリ クラスに属性を適用します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Outlook メッセージ クラスの概要  
 Outlook メッセージ クラスは、Outlook アイテムの種類を識別します。  8 種類の標準アイテムとそれに対応するメッセージ クラスの名前を次の表に示します。  
  
|Outlook アイテムの種類|メッセージ クラス名|  
|---------------------|----------------|  
|AppointmentItem|IPM.Appointment|  
|ContactItem|IPM.Contact|  
|DistListItem|IPM.DistList|  
|JournalItem|IPM.Activity|  
|MailItem|IPM.Note|  
|PostItem|IPM.Post or IPM.Post.RSS|  
|TaskItem|IPM.Task|  
  
 また、カスタム メッセージ クラスの名前を指定することもできます。  カスタム メッセージ クラスは、Outlook に定義したカスタム フォームを識別します。  
  
> [!NOTE]  
>  置換およびすべて置換のフォーム領域については、新しいカスタム メッセージ クラス名を指定できます。  既存のカスタム フォームのメッセージ クラス名を使用する必要はありません。  カスタム メッセージ クラスの名前は一意であることが必要です。  カスタム メッセージ クラス名を一意にする方法の 1 つに、\<*StandardMessageClassName*\>.\<*Company*\>.\<*MessageClassName*\> のような名前付け規則を使用することがあります \(この名前付け規則に従った名前は、IPM.Note.Contoso.MyMessageClass などになります\)。  
  
## フォーム領域の Outlook メッセージ クラスへの関連付け  
 フォーム領域をメッセージ クラスに関連付ける場合、次の 2 とおりの方法があります。  
  
-   **新しい Outlook フォーム領域**ウィザードの使用  
  
-   クラス属性の適用  
  
### 新しい Outlook フォーム領域ウィザードの使用  
 **新しい Outlook フォーム領域**ウィザードの最後のページで、標準のメッセージ クラスを選択し、フォーム領域に関連付けるカスタム メッセージ クラスの名前を入力できます。  
  
 フォーム全体またはフォームの既定のページに置き換わるフォーム領域では、標準のメッセージ クラスは使用できません。  標準のメッセージ クラスは、フォームに新しいページを追加するフォーム、またはフォームの下部に追加されるフォームでのみ指定できます。  詳細については、「[方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)」を参照してください。  
  
 1 つまたは複数のカスタム メッセージ クラスを含めるには、それらのクラス名を **\[このフォーム領域を表示するカスタム メッセージ クラスを選択\]** ボックスに入力します。  
  
 入力するクラス名は、以下のガイドラインに準拠している必要があります。  
  
-   メッセージ クラスの完全修飾名 \("IPM.Note.Contoso" など\) を使用します。  
  
-   複数のメッセージ クラス名を区切るには、セミコロンを使用します。  
  
-   "IPM.Note" や "IPM.Contact" などの標準の Outlook メッセージ クラスは含めません。  "IPM.Note.Contoso" などのカスタム メッセージ クラスのみ含めます。  
  
-   基本メッセージ クラス自体 \("IPM" など\) を指定しないでください。  
  
-   各メッセージ クラス名の長さは 256 文字を超えてはなりません。  
  
 **\[完了\]** をクリックすると、入力したメッセージ クラス名の形式が**新しい Outlook フォーム領域**ウィザードによって検証されます。  
  
> [!NOTE]  
>  **新しい Outlook フォーム領域**ウィザードでは、入力したメッセージ クラス名の正確性や有効性は検証されません。  
  
 **新しい Outlook フォーム領域**ウィザードが完了すると、指定したメッセージ クラス名を含む属性がフォーム領域クラスに適用されます。  これらの属性を手動で適用することもできます。  
  
### クラス属性の適用  
 **新しい Outlook フォーム領域**ウィザードを実行した後で、フォーム領域を Outlook メッセージ クラスに関連付けることができます。  これを行うには、属性をフォーム領域ファクトリ クラスに適用します。  
  
 次の例に、`myFormRegion` というフォーム領域ファクトリ クラスに適用された 2 つの <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> 属性を示します。  1 つ目の属性は、フォーム領域をメール メッセージ フォームの標準メッセージ クラスに関連付けます。  2 つ目の属性は、フォーム領域を `IPM.Task.Contoso` というカスタム メッセージ クラスに関連付けます。  
  
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/CS/FormRegion1.cs#1)]
 [!code-vb[Trin_Outlook_FR_Attributes#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/VB/FormRegion1.vb#1)]  
  
 属性は、以下のガイドラインに準拠している必要があります。  
  
-   カスタム メッセージ クラスには、完全修飾名 \("IPM.Note.Contoso" など\) を使用します。  
  
-   基本メッセージ クラス自体 \("IPM" など\) を指定しないでください。  
  
-   各メッセージ クラス名の長さは 256 文字を超えてはなりません。  
  
-   フォーム全体またはフォームの既定のページに置き換わるフォーム領域では、標準のメッセージ クラスの名前を含めません。  標準のメッセージ クラスは、フォームに新しいページを追加するフォーム、またはフォームの下部に追加されるフォームでのみ指定できます。  詳細については、「[方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)」を参照してください。  
  
 プロジェクトをビルドすると、Visual Studio によってメッセージ クラス名の形式が検証されます。  
  
> [!NOTE]  
>  Visual Studio では、入力したメッセージ クラス名の正確性や有効性は検証されません。  
  
## 参照  
 [実行時におけるフォーム領域へのアクセス](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [チュートリアル : Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Outlook フォーム領域の作成に関するガイドライン](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [フォームの名前とメッセージ クラスについて](HV01044315)   
 [Outlookがとどのように構成する項目が連携します](HV01044298)  
  
  