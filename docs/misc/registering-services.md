---
title: "サービスの登録 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービス、登録"
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# サービスの登録
オンデマンド読み込みをサポートするには、サービス プロバイダーはグローバル サービスを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に登録する必要があります。  
  
 開発時にマネージ サービス プロバイダーはパッケージのソース コードに属性を追加し、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE でパッケージを構築して、サービスとサービスのオーバーライドを登録します。 これにより、生成されたアセンブリで RegPkg.exe ユーティリティが実行され、パッケージの登録と配置の準備が行われます。 詳細については、「[方法: サービスを登録する](../misc/how-to-register-a-service.md)」を参照してください。  
  
 アンマネージ サービス プロバイダーは、提供するサービスをシステム レジストリのサービス セクションまたはサービス オーバーライド セクションで [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に登録する必要があります。 次の .reg ファイル フラグメントは、SVsTextManager サービスを登録する方法を示しています。  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
```  
  
 上記の例で、バージョン番号は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョン \(7.1 や 8.0 など\)、キー {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} は SVsTextManager サービスのサービス識別子 \(SID\)、既定値 {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} はサービスを提供するテキスト マネージャー VSPackage のパッケージ GUID です。  
  
## リモート サービスとバックグラウンド スレッド  
 提供するサービスは、リモートで、またはバックグラウンド スレッドに対して自動的に利用可能にはなりません。 使用できるようにするには、タイプ ライブラリを構築し、登録する必要があります。  
  
 Visual Studio ライブラリ \(VSL\) を使用するアンマネージ コードから、次のようにタイプ ライブラリを登録できます。  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE #include <VSLPackageDllEntryPoints.cpp>  
```  
  
 マネージ コードから、次のようにビルド後のステップを追加できます。  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## 参照  
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基礎](../extensibility/internals/service-essentials.md)