---
title: サービスの登録 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: f56c73bbb09c659a76083e511d79d487402477ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539996"
---
# <a name="registering-services"></a>サービスの登録
オンデマンド読み込みをサポートするサービス プロバイダーのグローバル サービスを登録する必要があります[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
 開発中は、マネージ サービス プロバイダーの登録サービスとサービスのオーバーライド、パッケージのソース コードに属性を追加しでパッケージを構築し、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE。 これにより、生成されたアセンブリで RegPkg.exe ユーティリティが実行され、パッケージの登録と配置の準備が行われます。 詳細については、次を参照してください。[方法: サービス登録](../misc/how-to-register-a-service.md)します。  
  
 非管理対象サービス プロバイダーに提供するサービスを登録する必要があります[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]サービスでセクションまたはサービスは、システム レジストリのセクションをオーバーライドします。 次の .reg ファイル フラグメントは、SVsTextManager サービスを登録する方法を示しています。  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 上記の例では、バージョン番号は、バージョンの[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]7.1 や 8.0 では、キー {f5e7e71d-1401-11d1-883b-0000f87579d2} は、サービス、SVsTextManager および既定値の {のサービス識別子 (SID) など、F5E7E720-1401-11d1-883B-0000F87579D2} は、テキスト マネージャー サービスを提供する VSPackage のパッケージ GUID です。  
  
## <a name="remote-services-and-background-threads"></a>リモート サービスとバックグラウンド スレッド  
 提供するサービスは、リモートで、またはバックグラウンド スレッドに対して自動的に利用可能にはなりません。 使用できるようにするには、タイプ ライブラリを構築し、登録する必要があります。  
  
 Visual Studio ライブラリ (VSL) を使用するアンマネージ コードから、次のようにタイプ ライブラリを登録できます。  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 マネージド コードから、次のようにビルド後のステップを追加できます。  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>関連項目  
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基本情報](../extensibility/internals/service-essentials.md)