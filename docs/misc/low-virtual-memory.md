---
title: "仮想メモリの不足 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aec803b1-9d76-46bb-8f14-8c63d80112a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 仮想メモリの不足
このメッセージは、仮想メモリが不足し、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] が応答を停止したときに発生します。  ただし、このエラーはコンピューターの仮想メモリが不足したときに発生するのではなく、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がアドレス空間を使い果たしているときに発生します。  通常、このエラーは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] が 2 GB のアドレス空間に制限される 32 ビット オペレーティング システムを実行しているコンピューター上で発生します。  32 ビット プロセスを使用する場合、アプリケーションは 4 GB のメモリ \(2^32 ビット\) だけをアドレス指定できます。  しかし、32 ビット バージョンの Windows では、内部処理 \(コンピューターのグラフィック カードや他のシステム ドライバーでの作業など\) 用に 2 GB の仮想アドレス空間が予約されています。  そのため、32 ビット プロセスがその内部処理用に使用できるのは 2 GB だけです。  \/3GB スイッチを設定すると、Windows 用に 1 GB だけが予約され、プロセスが 3 GB を使用できるようになります。  ほとんどの場合、Windows 用を 1 GB だけに制限しても、パフォーマンスは落ちません。  
  
 64 ビット バージョンの Windows を実行するシステムでは、プロセスが 4 GB のアドレス空間のすべてを使用でき、Windows はハードウェアおよびシステム ドライバーの処理用に 64 ビットのメモリ アドレスを使用できるため、このエラーはほとんど発生しません。  ただし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がいくつかのデータ セットを処理するときは、メモリの使用が 3 GB または 4 GB を超えることがあります。  詳細については、「[Visual Studio: Why is there no 64 bit version \(Visual Studio: 64 ビット バージョンがない理由\)](http://go.microsoft.com/fwlink/?LinkId=246307)」を参照してください。  
  
 通常、このエラーは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] が大量のデータをキャッシュしているときや、メモリを大量に消費する複数のプロセスを実行しているときに発生します。  
  
 次のシナリオには、大量のデータのキャッシングが伴います。通常は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を再起動することにより、この問題を解決できます。  
  
-   インストール後初めて、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行する。  
  
-   拡張機能をインストールまたはアンインストールする。  
  
-   **ツールボックス**のアイテムを選択またはカスタマイズする。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の設定を変更する。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を開いているときにシステムがスリープ \(ハイバネート\) モードに移行できるようにする。  
  
 次のシナリオでは、大量のアクティブ メモリが必要になります。  このような状況では、不可欠なコンポーネントのみを開いて [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行するか、または [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の 2 番目のインスタンスで追加のプロセスを実行することをお勧めします。  
  
-   大規模なソリューションを構築する。  
  
-   大きな XML ドキュメントを操作する。  
  
-   前のバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] からソリューションをアップグレードする。  
  
-   ソリューションのターゲットを再設定する。  
  
-   コードの編集中に [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] を実行する。  
  
-   複数のプロジェクトで IntelliTrace を実行する。  
  
 このような対策を講じてもエラーを回避できない場合は、bcedit.exe を次の構文で実行すると、[!INCLUDE[win7](../debugger/includes/win7_md.md)] を実行するシステムで使用できるアドレス空間を増やすことができます。  
  
 **bcdedit \/set IncreaseUserVa 3072**  
  
 このコマンドにより、x86 ベースのシステムでユーザー モード仮想メモリの割り当てが 2 GB から 3 GB に増えます。  \/3GB スイッチを追加すると、システム全体でより多くのメモリをアドレス指定でき、使用できるメモリのより多くの割合を各アプリケーションに提供できます。  
  
> [!NOTE]
>  bcdedit.exe は、管理アクセス許可で実行する必要があります。  BitLocker 暗号化が有効になっている場合は、Bitlocker を中断してから変更を加え、システムを再起動してから、再度 BitLocker を有効にする必要があります。  
  
 仮想メモリ アロケーションを 3 GB に増やした後でも、1 つのアプリケーションは仮想メモリを 2 GB しか使用できないため、このエラーが再発する可能性があります。  このエラーの発生が続く場合は、ソリューションのサイズを小さくして、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を再起動します。  ソリューションをリファクタリングして頻繁に使用されないプロジェクトを削除するか、不要なプロジェクトをアンロードすることで、ソリューションのサイズを小さくすることができます。  ソリューションのビルド時にエラーが発生する場合は、コマンド プロンプトでビルドしてみてください。  
  
## 参照  
 [Resources for Troubleshooting IDE Errors](../ide/reference/resources-for-troubleshooting-integrated-development-environment-errors.md)