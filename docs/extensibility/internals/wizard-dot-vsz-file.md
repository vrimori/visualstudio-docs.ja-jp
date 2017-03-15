---
title: "ウィザード (します。Vsz) ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f1dc3ff7964ea5290ffe926ef75773a7210b6449
ms.lasthandoff: 02/22/2017

---
# <a name="wizard-vsz-file"></a>ウィザード (します。Vsz) ファイル
統合開発環境 (IDE) では、.vsz ファイルを使用して、ウィザードを起動します。 これらの .vsz ファイルには、IDE を使用して呼び出すウィザードを決定する情報と、ウィザードに渡すには、どのような情報が含まれます。  
  
 .Vsz ファイルは、セクションが存在しません、.ini 形式のテキスト ファイルのバージョンです。 IDE に認識される情報は、ファイルの先頭に格納されます。 IDE を呼び出すウィザードとは、.vsz ファイルが IDE に渡されるパラメーターの間のリンクを提供します。 ファイルの残りの部分では、ウィザードに固有と、しを IDE で収集する、特定のウィザードに渡されるパラメーターを説明します。  
  
 次の例では、.vsz ファイルの内容を示します。  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 .Vsz ファイル内のパーツを次に示します。  
  
|パーツ|説明|  
|----------|-----------------|  
|VSWizard|ファイルの最初のパラメーターは、テンプレート ファイル形式のバージョン番号です。 このバージョン番号は 6.0、7.0、7.1、または 8.0 をする必要があります。 その他の番号を開始できませんエラーの原因と、形式が無効です。|  
|ウィザード|このフィールドには、OLE の ProgID ウィザード、または IDE で一緒ウィザードの CLSID の GUID の文字列形式が含まれています。|  
|Param|これらの部分は省略できます。 必要なだけ追加できます。|  
  
 パラメーターには、ウィザードに追加のカスタム パラメーターを渡す .vsz ファイルが有効にします。 それぞれの値は、variant の配列内の文字列要素としてウィザードに渡されます。 詳細については、次を参照してください。[カスタム パラメーター](../../extensibility/internals/custom-parameters.md)します。 カスタム ウィザードの開発に .vsz ファイルを使用する方法については、次を参照してください。[します。Vsz ファイル (プロジェクト コントロール)](/visual-cpp/ide/dot-vsz-file-project-control)  
  
 .Vsz ファイルには、既定のロケール ID を追加するには、指定`FALLBACK_LCID`= xxxx、ここで xxxx はロケール ID では、英語の場合は 1033 などです。 ときに`FALLBACK_LCID`パラメーターが定義されている、現在の ID が見つからない場合、ウィザードは指定されたフォールバック ロケール ID を使用しています。  
  
## <a name="see-also"></a>関連項目  
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [テンプレートのディレクトリの説明 (します。Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
