---
title: 従来の言語サービスの自動書式設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19c36f5a31c6d3ed7284922bc830ea4925da5833
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246728"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>従来の言語サービスの自動書式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

オート フォーマット、言語サービスでは、ユーザーが既知のコード コンストラクトの入力を開始するとのコード スニペットが自動的に挿入します。  
  
## <a name="automatic-formatting-behavior"></a>自動書式設定の動作  
 たとえば、「`if`言語サービスが自動的に一致する中かっこを挿入または、言語サービスが、かどうかに応じて、適切なインデント レベルに新しい行にカーソルを強制的場合は、ENTER キー押すと、前に、行は、新しいスコープが表示されます。  
  
 言語サービスの残りの部分に使用されるコマンドのフィルターは、自動書式設定するためも使用できます。 呼び出すことによって、対応する中かっこを強調することも<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>します。  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)

