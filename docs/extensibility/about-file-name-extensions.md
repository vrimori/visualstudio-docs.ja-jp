---
title: ファイル名拡張子 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2c940319cd0ce3204f6dd9bb62e731de49b8baac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108470"
---
# <a name="about-file-name-extensions"></a>ファイル名の拡張機能の概要
VSPackage のファイル拡張子を登録するときに関連付けることが、バージョンの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 これは、1 つのバージョン以上の場合に重要な[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コンピューターにインストールします。  
  
 Vspackage のファイル拡張子は、既定値は、関連付けられているプログラム id (ProgID) を指す HKEY_CLASSES_ROOT キーの下に登録されます。  
  
 .Vcproj ファイル拡張機能の登録情報の例を次に示します。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 関連付けられたファイル[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]必要があります、バージョン管理された ProgID など`VisualStudio.vcproj.8.0`製品のバージョン間でファイル拡張子の関連付けを維持するために製品のサイド バイ サイド インストールを許可します。 バージョン固有の ProgID では、オープン、編集などと上書きやその他のアプリケーションまたはのバージョンで上書きされるの気にせずに、標準の動詞を使用することもできます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
 場合によっては、ファイル拡張子に関連付けられた ProgID が変更されません。 ファイル拡張子が .htm の ProgID など (progid htmlfile =) は、さまざまなオペレーティング システムの場所にハードコーディングされて、.htm と .html ファイルで広く知られで使用される関連付けであります。  
  
## <a name="see-also"></a>関連項目  
 [サイド バイ サイド配置のファイル名拡張子を登録します。](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [ファイル名拡張子のファイル ハンドラーを指定する](../extensibility/specifying-file-handlers-for-file-name-extensions.md)