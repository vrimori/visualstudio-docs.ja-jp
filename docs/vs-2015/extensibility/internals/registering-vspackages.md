---
title: Vspackage の登録 |Microsoft Docs
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
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6bbfc837323ddb103405ab289e89322ddb344040
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243569"
---
# <a name="registering-vspackages"></a>VSPackage の登録
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .pkgdef ファイルを記述し、VSPackage の検索に依存します。 .Pkgdef ファイルには、それ以外の場合は、システム レジストリに追加するすべての登録情報が含まれています。 マネージ Vspackage が、ソース コードに属性を追加して実行し、登録されている、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md).pkgdef ファイルを生成する結果として得られるアセンブリ。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [VSPackage ファイルの場所を VS Shell に指定する](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Vspackage、読み込みパスをについて説明します。  
  
 [VSPackage の登録と登録解除](../../extensibility/registering-and-unregistering-vspackages.md)  
 VSPackage を登録する方法について説明します。  
  
 [カスタム登録属性を使用した拡張機能の登録](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 マネージ VSPackage の配置に使用できる登録マニフェストを作成する方法について説明します。

