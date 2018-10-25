---
title: ウィザード (します。Vsz) ファイル |Microsoft Docs
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
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1d8d36ba617f5d5828354e32b5b0f45ed9ec1ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197170"
---
# <a name="wizard-vsz-file"></a>ウィザード (.Vsz) ファイル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

統合開発環境 (IDE) では、ウィザードを起動するのに .vsz ファイルを使用します。 これらの .vsz ファイルには、IDE を使用してを呼び出すには、どのウィザードを決定する情報と、ウィザードに渡す場合は、どのような情報が含まれます。  
  
 .Vsz ファイルは、セクションがない .ini 形式のテキスト ファイルのバージョンです。 IDE に既知の情報は、ファイルの先頭に格納されます。 これは、ウィザード、IDE を呼び出すと、IDE に渡される .vsz ファイル内にあるパラメーター間のリンクを提供します。 ファイルの残りの部分では、ウィザードに固有と、し、IDE によって収集されるように、特定のウィザードに渡されるパラメーターを提供します。  
  
 次の例では、.vsz ファイルの内容を示します。  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 .Vsz ファイルの部分を次に示します。  
  
|パーツ|説明|  
|----------|-----------------|  
|VSWizard|ファイルの最初のパラメーターは、テンプレート ファイルの形式のバージョン番号です。 このバージョン番号は、6.0、7.0、7.1、または 8.0 である必要があります。 他の数値は、開始することはできません、形式が無効ですエラーが発生します。|  
|ウィザード|このフィールドには、OLE の ProgID ウィザード、または、IDE によって一緒はウィザードの CLSID の GUID の文字列表現が含まれています。|  
|Param|これらの部分は省略可能です。 必要な数だけ追加できます。|  
  
 パラメーターには、ウィザードに追加のカスタム パラメーターを渡す .vsz ファイルが有効にします。 各値は、variant の配列内の文字列要素としてウィザードに渡されます。 詳細については、次を参照してください。[カスタム パラメーター](../../extensibility/internals/custom-parameters.md)します。 開発のカスタム ウィザードの .vsz ファイルを使用する方法については、次を参照してください。[します。Vsz ファイル (プロジェクト コントロール)](http://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 .Vsz ファイルには、既定のロケール ID を追加するには、指定`FALLBACK_LCID`= xxxx, ここで xxxx は、ロケール ID を英語の場合は 1033 など。 ときに`FALLBACK_LCID`パラメーターが定義されている場合、ウィザードは、現在の ID が見つからない場合に指定されたフォールバック ロケール ID を使用します。  
  
## <a name="see-also"></a>関連項目  
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [テンプレート ディレクトリの説明 (.Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

