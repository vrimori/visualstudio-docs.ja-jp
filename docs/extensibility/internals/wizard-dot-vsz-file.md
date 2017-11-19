---
title: "ウィザード (です。Vsz) ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7f4abe6240f799ed6db71fcf04a40774facaf6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-vsz-file"></a>ウィザード (です。Vsz) ファイル
統合開発環境 (IDE) では、.vsz ファイルを使用して、ウィザードを起動します。 これらの .vsz ファイルには、IDE を使用して呼び出すウィザードを決定する情報と、ウィザードに渡すには、どのような情報が含まれます。  
  
 .Vsz ファイルは、セクションがない .ini 形式のテキスト ファイルのバージョンです。 IDE に既知の情報は、ファイルの先頭に格納されます。 これは、ウィザード、IDE を呼び出すと、IDE に渡される .vsz ファイル内にあるパラメーターの間のリンクを提供します。 ファイルの残りの部分では、ウィザードに固有であるとを IDE で収集するのには、特定のウィザードに渡されるパラメーターを提供します。  
  
 .Vsz ファイルの内容を次の例に示します。  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 .Vsz ファイル内のパーツを次に示します。  
  
|パーツ|説明|  
|----------|-----------------|  
|VSWizard|ファイルの最初のパラメーターは、テンプレート ファイル形式のバージョン番号です。 このバージョン番号には、6.0、7.0、7.1、8.0 またはを指定する必要があります。 その他の番号を開始できませんエラーの原因と、形式が無効です。|  
|ウィザード|このフィールドには、OLE の ProgID ウィザード、または IDE によって一緒、ウィザードの CLSID の GUID の文字列表現が含まれています。|  
|Param|これらの部分は省略できます。 必要な追加できます。|  
  
 パラメーターには、ウィザードに追加のカスタム パラメーターを渡す .vsz ファイルが有効にします。 各値は、variant の配列内の文字列要素として、ウィザードに渡されます。 詳細については、次を参照してください。[カスタム パラメーター](../../extensibility/internals/custom-parameters.md)です。 カスタム ウィザードの開発に .vsz ファイルを使用する方法については、次を参照してください。[です。Vsz ファイル (プロジェクト コントロール)](/cpp/ide/dot-vsz-file-project-control)  
  
 .Vsz ファイルに既定のロケール ID を追加するには、指定`FALLBACK_LCID`xxxx、ここで xxxx は、ロケール ID を英語の場合は 1033 などを = です。 ときに`FALLBACK_LCID`パラメーターが定義されている場合、ウィザードは、現在の ID が見つからない場合に、フォールバック ロケールの指定された ID を使用します。  
  
## <a name="see-also"></a>関連項目  
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [テンプレート ディレクトリの説明 (.Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)