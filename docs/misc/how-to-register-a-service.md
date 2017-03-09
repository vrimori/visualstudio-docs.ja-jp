---
title: "方法: サービスを登録する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービス、登録"
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 方法: サービスを登録する
Managed Package Framework \(MPF\) は、管理するサービスの登録を制御する属性を提供します。 RegPkg ユーティリティでは、これらの属性を使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] にサービスを登録します。  
  
## 使用例  
 その後のコードは、[VSSDK のサンプル](../misc/vssdk-samples.md) から取得されます。  
  
 [!code-vb[VSSDKRegisterService#1](../misc/codesnippet/VisualBasic/how-to-register-a-service_1.vb)]
 [!code-cs[VSSDKRegisterService#1](../misc/codesnippet/CSharp/how-to-register-a-service_1.cs)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> によって、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に SMyGlobalService サービスが登録されます。<xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> および <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> の詳細については、「[Vspackage の登録と登録解除しています](../extensibility/registering-and-unregistering-vspackages.md)」を参照してください。  
  
 名前が同じ別のサービスを置き換えるサービスを登録するには、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> ではなく <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> を使用します。  
  
## 信頼性の高いプログラミング  
 サービス クライアントを変更せずに、サービス プロバイダーの再コンパイルを容易にできるようにするか、またはその逆を実行するには、別のアセンブリ モジュールでサービスとそのインターフェイスを定義することができます。 次のコードは Reference.Services \(C\#\) サンプルの IMyGlobalService.cs ファイルのものです。  
  
 [!code-vb[VSSDKRegisterService#2](../misc/codesnippet/VisualBasic/how-to-register-a-service_2.vb)]
 [!code-cs[VSSDKRegisterService#2](../misc/codesnippet/CSharp/how-to-register-a-service_2.cs)]  
  
 アンマネージ コードからインターフェイスを取得するには、<xref:System.Runtime.InteropServices.ComVisibleAttribute> が必要です。  
  
> [!NOTE]
>  サービスとインターフェイスの両方に同じ型または GUID を使用できますが、サービスが異なるインターフェイスを公開できるようにするために、2 つを分離することをお勧めします。  
  
## 参照  
 [Registering VSPackages](http://msdn.microsoft.com/ja-jp/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [サービスの基礎](../extensibility/internals/service-essentials.md)