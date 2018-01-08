---
title: "従来の言語サービスで自動書式 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 43d9c59beaddfc6992e7b9e16e0e778be2a6d30f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>自動レガシ言語サービスで書式設定
自動書式を使用する言語サービスでは、ユーザーは、既知のコード構成体の入力を開始するとコード スニペットが自動的に挿入します。  
  
## <a name="automatic-formatting-behavior"></a>自動の書式設定動作  
 たとえば、「`if`言語サービスが自動的に一致する中かっこを挿入、または言語サービスが、どうかに応じて、適切なインデント レベルに新しい行カーソルを強制的場合は、ENTER キーを押す前述の行は、新しいスコープを開きます。  
  
 言語サービスの残りの部分に使用されるコマンドのフィルターは、オート フォーマットも使用できます。 呼び出すことによって、対応する中かっこを強調することも<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>します。  
  
## <a name="see-also"></a>参照  
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)