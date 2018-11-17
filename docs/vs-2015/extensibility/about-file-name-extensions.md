---
title: ファイル名拡張子について |Microsoft Docs
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
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 680f9e9f79430ea53da3566686b058c44894e494
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776084"
---
# <a name="about-file-name-extensions"></a>ファイル名拡張子について
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

バージョンを関連付ける場合、VSPackage のファイル拡張子を登録するときに[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 これは、1 つのバージョンではより重要な場合は[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]をコンピューターにインストールされます。  
  
 Vspackage のファイル拡張子は、既定値は関連付けられているなプログラム識別子 (ProgID) を指す HKEY_CLASSES_ROOT キーの下に登録されます。  
  
 .Vcproj ファイル拡張機能の登録情報の例を次に示します。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 ファイルに関連付けられている[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]バージョン管理された ProgID などがあります`VisualStudio.vcproj.8.0`製品のバージョン間でファイル拡張子の関連付けを維持するために、製品のサイド バイ サイドでインストールを許可します。 バージョン固有の ProgID では、オープン、編集などと、上書きやその他のアプリケーションまたはのバージョンで上書きされるの気にせず、標準の動詞を使用することもできます[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
 場合によっては、ファイル拡張子に関連付けられている ProgID を変更しない必要があります。 .Htm ファイル拡張子の ProgID など (progid = htmlfile) .htm と .html ファイル関連付け広く知られ使用であり、さまざまなオペレーティング システムの場所にハードコーディングされています。  
  
## <a name="see-also"></a>関連項目  
 [サイド バイ サイドで配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [ファイル名拡張子のファイル ハンドラーを指定する](../extensibility/specifying-file-handlers-for-file-name-extensions.md)

