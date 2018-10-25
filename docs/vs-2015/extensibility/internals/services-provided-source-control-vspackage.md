---
title: 提供されるサービス (ソース管理 VSPackage) |Microsoft Docs
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
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee980b74415d906a5c48cfd5ad1e20e7b5544320
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273378"
---
# <a name="services-provided-source-control-vspackage"></a>提供されるサービス (ソース管理 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

サービスは、Vspackage 間および Visual Studio 統合開発環境 (IDE) と、インストールされている Vspackage 間に共有する機能により、主要なメカニズムです。 サービスと、Visual Studio IDE で、重要度の詳細については、次を参照してください。[を使用すると、サービスを提供する](../../extensibility/using-and-providing-services.md)します。  
  
## <a name="the-source-control-service"></a>ソース管理サービス  
 Visual Studio では、サービス、IDE レベルのサービスおよびパッケージ レベルのサービスの 2 つのレイヤーを提供します。 Visual Studio IDE は、ネイティブ IDE レベルのサービスを提供します。 ソース管理パッケージは、これらのサービスの一部を消費します。 VSPackage としてソース管理パッケージでは、独自の秘密のソース管理サービスを提供することで、ソース管理機能を共有します。 ソース管理パッケージは、Visual Studio IDE で使用できるコントラクトの形式でによって実装されるソース コントロールに関連するインターフェイスのセットをカプセル化します。  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)

