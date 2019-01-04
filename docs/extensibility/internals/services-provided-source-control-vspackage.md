---
title: 提供されるサービス (ソース管理 VSPackage) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5cbc107b1b300538cf9a94a89a77d8ac9e2ff728
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828538"
---
# <a name="services-provided-source-control-vspackage"></a>提供されるサービス (ソース管理 VSPackage)
サービスは、Vspackage 間および Visual Studio 統合開発環境 (IDE) と、インストールされている Vspackage 間に共有する機能により、主要なメカニズムです。 サービスと、Visual Studio IDE で、重要度の詳細については、次を参照してください。[を使用すると、サービスを提供する](../../extensibility/using-and-providing-services.md)します。  
  
## <a name="the-source-control-service"></a>ソース管理サービス  
 Visual Studio では、サービス、IDE レベルのサービスおよびパッケージ レベルのサービスの 2 つのレイヤーを提供します。 Visual Studio IDE は、ネイティブ IDE レベルのサービスを提供します。 ソース管理パッケージは、これらのサービスの一部を消費します。 VSPackage としてソース管理パッケージでは、独自の秘密のソース管理サービスを提供することで、ソース管理機能を共有します。 ソース管理パッケージは、Visual Studio IDE で使用できるコントラクトの形式でによって実装されるソース コントロールに関連するインターフェイスのセットをカプセル化します。  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)