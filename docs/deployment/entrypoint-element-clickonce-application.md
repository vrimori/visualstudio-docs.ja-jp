---
title: "&lt;entryPoint&gt; 要素 (ClickOnce アプリケーション) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<entryPoint> 要素 [ClickOnce アプリケーション マニフェスト]"
  - "マニフェスト [ClickOnce], entryPoint 要素"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# &lt;entryPoint&gt; 要素 (ClickOnce アプリケーション)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションをクライアント コンピューター上で実行するときに実行されるアセンブリを指定します。  
  
## 構文  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## 要素と属性  
 `entryPoint` 要素は必須です。この要素は `urn:schemas-microsoft-com:asm.v2` 名前空間にあります。  アプリケーション マニフェストには `entryPoint` 要素を 1 つだけ定義できます。  
  
 `entryPoint` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`name`|省略可能です。  この値は .NET Frameworkでは使用されません。|  
  
 `entryPoint` には、以下の要素があります。  
  
## assemblyIdentity  
 必ず指定します。  `assemblyIdentity` の役割および属性は、「[\<assemblyIdentity\> 要素](../deployment/assemblyidentity-element-clickonce-application.md)」で定義されています。  
  
 この要素の `processorArchitecture` 属性と、アプリケーション マニフェストの別の場所で `assemblyIdentity` に定義されている `processorArchitecture` 属性は、一致している必要があります。  
  
## commandLine  
 必ず指定します。  `entryPoint` 要素の子である必要があります。  子要素は持たず、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`file`|必ず指定します。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのスタートアップ アセンブリへのローカル参照です。  この値には、フォワード スラッシュ \(\/\) またはバックスラッシュ \(\\\) のパス区切り記号を含めることができません。|  
|`parameters`|必ず指定します。  エントリ ポイントで実行するアクションを説明します。  唯一の有効な値は `run` です。空白文字列を指定した場合、`run` が指定されていると仮定されます。|  
  
## customHostRequired  
 省略可能です。  この属性を含めると、配置には、カスタム ホストの内側に配置されるコンポーネントが含まれ、スタンドアロン アプリケーションではないことを指定できます。  
  
 この要素を指定する場合、`assemblyIdentity` 要素と `commandLine` 要素は指定できません。  これらの要素を指定すると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] によって、インストール中に妥当性確認エラーが表示されます。  
  
 この要素には、属性も子もありません。  
  
## customUX  
 省略可能です。  カスタム インストーラーによってアプリケーションがインストールおよび保守されることを示します。また、\[スタート\] メニュー エントリ、ショートカット、\[プログラムの追加または削除\] エントリは作成されません。  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 customUX 要素を含むアプリケーションは、<xref:System.Deployment.Application.InPlaceHostingManager> クラスを使用してインストール操作を実行するカスタム インストーラーを用意する必要があります。  この要素を使用するアプリケーションは、マニフェストや setup.exe の必須コンポーネント ブートストラップをダブルクリックする方法でインストールすることはできません。  カスタム インストーラーによって、\[スタート\] メニュー エントリ、ショートカット、\[プログラムの追加または削除\] エントリを作成できます。  カスタム インストーラーによって \[プログラムの追加または削除\] エントリを作成しない場合、<xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> プロパティが示すサブスクリプション識別子を保存し、ユーザーが <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> メソッドを呼び出して後でアプリケーションをアンインストールできるようにする必要があります。  詳細については、「[チュートリアル: ClickOnce アプリケーションのカスタム インストーラーの作成](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)」を参照してください。  
  
## 解説  
 この要素は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのアセンブリおよびエントリ ポイントを識別します。  
  
 実行時に `commandLine` を使用して、アプリケーションにパラメーターを渡すことはできません。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置のクエリ文字列パラメーターには、アプリケーションの <xref:System.AppDomain> からアクセスできます。  詳細については、「[方法 : オンライン ClickOnce アプリケーションでクエリ文字列を取得する](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md)」を参照してください。  
  
## 使用例  
 次のコード例は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのアプリケーション マニフェスト内の `entryPoint` 要素を示しています。  このコード例は、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」で使用されているより詳細な例の一部です。  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## 参照  
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)