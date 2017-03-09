---
title: "方法: GetGlobalService を使用する | Microsoft Docs"
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
  - "サービス、GetGlobalService"
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 方法: GetGlobalService を使用する
コントロールとツール ウィンドウ コンテナーからサービスを取得する必要があるに配置されていないできますがまたは必要なサービスについて認識サービス プロバイダーとに配置されています。  たとえばコントロールの内部からアクティビティ ログに書き込む必要がある場合があります。  これらのプロパティおよびそのほかのシナリオの詳細については[方法: サービスのトラブルシューティング](../extensibility/how-to-troubleshoot-services.md) を参照してください。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> の静的メソッドを呼び出して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のほとんどのサービスを取得できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> は <xref:Microsoft.VisualStudio.Shell.Package> から派生するどの VSPackage を配置する前に初期化キャッシュされたサービス プロバイダーに依存します。  この条件が保証されnull またはサービスに対して満たされていることを準備する必要があります。  
  
 しかし<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> は通常は正しく動作します。  
  
-   VSPackage が別の VSPackage にのみ取得できるサービスを提供する場合サービスを要求する VSPackage はサービスを提供する VSPackage の読み込み前にを配置されます。  
  
-   VSPackage でツール ウィンドウを作成するとVSPackage はツール ウィンドウを作成する前にを配置されます。  
  
-   コントロール コンテナーが VSPackage で作成されたツール ウィンドウでホストされる VSPackage はコントロール コンテナーが作成される前にを配置されます。  
  
### サービスをから取得するツール ウィンドウまたはコントロール コンテナー  
  
-   コンストラクターツール ウィンドウまたはコントロール コンテナーでこのコードを挿入します :  
  
     [!code-vb[UseGetGlobalService#1](../misc/codesnippet/VisualBasic/how-to-use-getglobalservice_1.vb)]
     [!code-cs[UseGetGlobalService#1](../misc/codesnippet/CSharp/how-to-use-getglobalservice_1.cs)]  
  
     このコードは SVsActivityLog のサービスを取得しアクティビティ ログに書き込むために使用できる <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> のインターフェイスにキャストします。  例については、「[方法: 動作状況ログの使用](../extensibility/how-to-use-the-activity-log.md)」を参照してください。  
  
## 参照  
 [方法: サービスのトラブルシューティング](../extensibility/how-to-troubleshoot-services.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基礎](../extensibility/internals/service-essentials.md)