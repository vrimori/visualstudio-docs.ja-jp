---
title: '方法: サービス登録 |Microsoft Docs'
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
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: a242a13893c7cd303adfe266c9609b7a71d251ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537656"
---
# <a name="how-to-register-a-service"></a>方法: サービスを登録する
Managed Package Framework (MPF) は、管理するサービスの登録を制御する属性を提供します。 RegPkg ユーティリティでは、これらの属性を使用して、使用済みのサービスを登録する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
## <a name="example"></a>例  
 次のコードは[VSSDK のサンプル](../misc/vssdk-samples.md)します。  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> SMyGlobalService サービスを登録します[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 詳細については<xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute>と<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>を参照してください[の登録および登録を解除する Vspackage](../extensibility/registering-and-unregistering-vspackages.md)します。  
  
 同じ名前の別のサービスを置換するサービスを登録するには、使用、<xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>の代わりに、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 サービス クライアントを変更せずに、サービス プロバイダーの再コンパイルを容易にできるようにするか、またはその逆を実行するには、別のアセンブリ モジュールでサービスとそのインターフェイスを定義することができます。 次のコードは Reference.Services (C#) サンプルの IMyGlobalService.cs ファイルのものです。  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>アンマネージ コードからインターフェイスを取得するが必要です。  
  
> [!NOTE]
>  サービスとインターフェイスの両方に同じ型または GUID を使用できますが、サービスが異なるインターフェイスを公開できるようにするために、2 つを分離することをお勧めします。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage の登録](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [サービスの基本情報](../extensibility/internals/service-essentials.md)