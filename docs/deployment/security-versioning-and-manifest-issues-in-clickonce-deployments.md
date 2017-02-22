---
title: "ClickOnce 配置でのセキュリティ、バージョン管理、およびマニフェストの問題 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce アプリケーション, マニフェストに関する問題"
  - "ClickOnce アプリケーション, セキュリティ問題"
  - "ClickOnce アプリケーション, バージョン管理に関する問題"
  - "ClickOnce アプリケーション, Windows Vista ユーザー アカウント制御"
  - "マニフェスト [ClickOnce]"
  - "セキュリティ, ClickOnce アプリケーション"
  - "ユーザー アカウント制御, ClickOnce アプリケーション"
  - "バージョン管理, ClickOnce アプリケーション"
  - "Windows 7, ClickOnce 配置"
  - "Windows Vista, ClickOnce 配置"
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce 配置でのセキュリティ、バージョン管理、およびマニフェストの問題
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、セキュリティ、アプリケーションのバージョン管理、およびマニフェストの構文やセマンティクスに関連するさまざまな問題によって、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置が失敗する可能性があります。  
  
## ClickOnce と Windows Vista のユーザー アカウント制御  
 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] では、既定で、アプリケーションは標準ユーザーとして実行されます。これは、現在のユーザーが管理者のアクセス許可のあるアカウントを使用してログインしている場合でも同様です。  アプリケーションで管理者のアクセス許可が必要なアクションを実行する必要がある場合、アプリケーションからオペレーティング システムに通知され、オペレーティング システムではユーザーに管理者の資格情報を入力するように求めるプロンプトを表示します。  この機能は、ユーザー アカウント制御 \(UAC: User Account Control\) と呼ばれ、ユーザーの明示的な承認なしに、オペレーティング システム全体に影響する可能性のある変更をアプリケーションが加えることのないようにします。  Windows アプリケーションは、アプリケーション マニフェストの `trustInfo` セクションに `requestedExecutionLevel` 属性を指定することで、アクセス許可の昇格を求めることを宣言します。  
  
 アプリケーションがセキュリティ昇格攻撃の危険にさらされる可能性があるため、UAC がクライアントに対して有効である場合に、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションがアクセス許可の昇格を要求することはできません。  `requestedExecutionLevel` 属性を `requireAdministrator` または `highestAvailable` に設定することを試みる [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、どのようなアプリケーションであっても、[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] にインストールされません。  
  
 場合によっては、[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 上のインストーラーの検出ロジックに基づいて、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションが管理者のアクセス許可での実行を試みることがあります。  この場合、アプリケーション マニフェストの `requestedExecutionLevel` 属性を `asInvoker` に設定できます。  これにより、昇格せずにアプリケーション自体を実行できます。この属性は、[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] によって自動的にすべてのアプリケーション マニフェストに追加されます。  
  
 アプリケーションの実行中に管理者のアクセス許可を要求するアプリケーションを開発する場合は、アプリケーションの配置に Windows インストーラー \(MSI\) テクノロジの使用を検討する必要があります。  詳細については、「[Windows インストーラーの基本概念](../extensibility/internals/windows-installer-basics.md)」を参照してください。  
  
## オンライン アプリケーションのクォータと部分信頼アプリケーション  
 インストール ベースではなくオンラインで動作する [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは、オンライン アプリケーション専用のクォータに収まる必要があります。  また、セキュリティ アクセス許可の制限されたセットなどの部分信頼で動作するネットワーク アプリケーションは、クォータ サイズの半分を超えることはできません。  
  
 オンライン アプリケーションのクォータを変更する方法と処理手順の詳細については、「[ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)」を参照してください。  
  
## バージョン管理に関する問題  
 アセンブリに厳密な名前を付けていて、アプリケーションの更新を反映するようにアセンブリのバージョン番号をインクリメントした場合には、問題が発生する可能性があります。  厳密な名前のアセンブリを参照してコンパイルされている各アセンブリは、再コンパイルする必要があります。再コンパイルしないと、古いバージョンが参照されます。  アセンブリがそのように動作するのは、バインド要求で古いバージョン値を使用しているためです。  
  
 たとえば、厳密な名前のアセンブリがあり、そのアセンブリのプロジェクトでのバージョンが 1.0.0.0 であるとします。  このアセンブリをコンパイルしてから、メイン アプリケーション用のプロジェクトに、このアセンブリを参照として追加します。  アセンブリを更新し、バージョンを 1.0.0.1 にインクリメントしてから、アプリケーションを再コンパイルしないでこのアセンブリを配置すると、アプリケーションの実行時にこのアセンブリを読み込むことができなくなります。  
  
 このエラーは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] マニフェストを手動で編集した場合にだけ発生します。[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] を使用して配置を作成する場合には、このエラーは発生しません。  
  
## マニフェストでの個々の .NET Framework アセンブリの指定  
 古いバージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] アセンブリを参照するように [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を手動で編集すると、アプリケーションが読み込みに失敗します。  たとえば、マニフェストに指定されたバージョンよりも古いバージョンの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の System.Net アセンブリへの参照を追加すると、エラーが発生します。  アプリケーションの実行対象である [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンは、アプリケーション マニフェストに依存関係として指定されるため、一般には個々の [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] アセンブリへの参照を指定しないようにする必要があります。  
  
## マニフェストの解析に関する問題  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] が使用するマニフェスト ファイルは、XML ファイルであり、整形式かつ有効である必要があります。つまり、これらの XML ファイルは XML 構文の規則に従っており、関連する XML スキーマで定義された要素と属性だけを使用している必要があります。  
  
 マニフェスト ファイルで問題が発生する原因の 1 つに、単一引用符または二重引用符などの特殊文字を含んだ名前をアプリケーションに付けることが挙げられます。  アプリケーションの名前は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の ID の一部です。  現在、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] では、特殊文字を含む ID を解析しません。  アプリケーションをアクティブ化できない場合は、名前に英数字のみを使用しているかどうかを確認し、再度配置を試みてください。  
  
 手動で配置マニフェストまたはアプリケーション マニフェストを編集すると、意図しない破損を招く可能性があります。  マニフェストが破損していると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のインストールが正しく行われません。  **\[ClickOnce エラー\]** ダイアログ ボックスの **\[詳細\]** をクリックし、ログに記録されたエラー メッセージを読めば、そのような誤りを実行時にデバッグできます。  このログには、次のいずれかのメッセージが記録されます。  
  
-   構文エラーの説明、およびエラーが発生した行の行番号と文字位置。  
  
-   マニフェストのスキーマに違反して使用されている要素または属性の名前。  マニフェストに XML を手動で追加した場合には、追加した内容をマニフェストのスキーマと照合する必要があります。  詳細については、「[ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)」および「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」を参照してください。  
  
-   競合している ID。  配置マニフェストおよびアプリケーション マニフェスト内で参照する依存関係は、`name` 属性と `publicKeyToken` 属性とが、一意である必要があります。  マニフェスト内のいずれかの 2 つの要素の間で、両方の属性が一致した場合、マニフェストの解析は失敗します。  
  
## マニフェストまたはアプリケーションを手動で変更するときの注意事項  
 アプリケーション マニフェストを更新するときには、アプリケーション マニフェストと配置マニフェストの両方を再署名する必要があります。  配置マニフェストには、アプリケーション マニフェストへの参照が含まれており、そのファイルのハッシュとデジタル署名が格納されています。  
  
### 配置プロバイダーの使用に関する注意事項  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の配置マニフェストには、アプリケーションのインストール元およびサービス提供元となる場所の完全パスを示す、次のような `deploymentProvider` プロパティがあります。  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 このパスは [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] がアプリケーションを作成するときに設定され、インストール済みアプリケーションには必須です。  このパスが指す先は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のインストーラーによるアプリケーションのインストール元の標準の場所であり、更新プログラムを検索する標準の場所です。  **xcopy** コマンドを使用して [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを別の場所にコピーしたときに `deploymentProvider` プロパティを変更しないと、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は元の場所をそのまま参照してアプリケーションのダウンロードを試みます。  
  
 アプリケーションを移動またはコピーするときは、必ず `deploymentProvider` のパスも変更して、クライアントが新しい場所からインストールを実行できるようにする必要があります。  このパスの更新は、主にインストール済みアプリケーションの場合に関係します。  常に元の URL から起動されるオンライン アプリケーションでは、`deploymentProvider` の設定を省略できます。  `deploymentProvider` が設定されていればそれに従いますが、設定されていない場合は、アプリケーションの起動に使用される URL が、アプリケーション ファイルをダウンロードするためのベース URL として使用されます。  
  
> [!NOTE]
>  マニフェストは、更新のたびに必ず再度署名する必要があります。  
  
## 参照  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)