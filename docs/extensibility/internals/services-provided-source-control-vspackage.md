---
title: "提供されるサービス (ソース コントロール VSPackage) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6951881e915b44c0cb0c85685280f2b770647f3a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="services-provided-source-control-vspackage"></a>提供されるサービス (ソース コントロール VSPackage)
サービスは、Vspackage 間および Visual Studio 統合開発環境 (IDE) と、インストールされている Vspackage 間に機能を共有する主要なメカニズムです。 サービスと、Visual Studio IDE の重要度の詳細については、次を参照してください。[を使用するとサービスを提供する](../../extensibility/using-and-providing-services.md)です。  
  
## <a name="the-source-control-service"></a>ソース管理サービス  
 Visual Studio には、サービス、IDE レベルのサービスおよびパッケージ レベルのサービスの 2 つのレイヤーが用意されています。 Visual Studio IDE は、ネイティブ IDE レベルのサービスを提供します。 ソース管理パッケージでは、これらのサービスの一部を消費します。 VSPackage としてソース管理パッケージでは、独自のプライベートはソース管理サービスを提供することにより、ソース管理機能を共有します。 ソース管理パッケージは、Visual Studio IDE で使用できるコントラクトの形式でによって実装されたソース コントロールに関連するインターフェイスのセットをカプセル化します。  
  
## <a name="see-also"></a>参照  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)