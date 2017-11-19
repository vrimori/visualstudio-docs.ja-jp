---
title: "VSPackage の登録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 263e2adf69aa479974a07dbb2acc2d4cd8f2a0dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="vspackage-registration"></a>VSPackage の登録
Vspackage をアドバイスする必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]読み込めますがインストールされ、必要があります。 このプロセスは、レジストリで情報を記述して実行します。 インストーラーの一般的なジョブです。  
  
> [!NOTE]
>  自己登録を使用する VSPackage の開発時に、許容される方法です。 ただし、[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)]パートナーは、セットアップの一部として自己登録を使用して製品を出荷できません。  
  
 Windows インストーラー パッケージ内のレジストリ エントリは、レジストリの表に一般的に行われます。 レジストリの表に、ファイル拡張子を登録することもできます。 ただし、Windows インストーラーは、プログラム id (ProgId)、クラス、拡張機能、および動詞テーブルを組み込みサポートを提供します。 詳細については、次を参照してください。[データベース テーブル](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)です。  
  
 レジストリ エントリは、選択したサイド バイ サイド戦略を適切なコンポーネントに関連付けられていることを確認します。 たとえば、共有ファイルのレジストリ エントリは、そのファイルの Windows インストーラーのコンポーネントに関連付けする必要があります。 同様に、バージョン固有のファイルのレジストリ エントリは、そのファイルのコンポーネントに関連付けする必要があります。 それ以外の場合、インストールまたはの 1 つのバージョンについては、VSPackage をアンインストールする[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]他のバージョンで、VSPackage を中断する可能性があります。 詳細については、次を参照してください[をサポートする複数のバージョンの Visual Studio。](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  登録を管理する最も簡単な方法は、開発者の登録とインストール時の登録の両方に同じファイルで、同じデータを使用します。 たとえば、インストーラーの開発ツールによっては、ビルド時に .reg 形式でファイルを使用できます。 開発者が独自の日常的な開発の .reg ファイルを維持すると、デバッグは、同じファイルに指定するインストーラーに自動的にします。 登録データを自動的に共有することはできない場合は、登録データのインストーラーのコピーが最新であることを確認する必要があります。  
  
## <a name="registering-unmanaged-vspackages"></a>アンマネージ Vspackage を登録します。  
 アンマネージ Vspackage を (Visual Studio パッケージ テンプレートによって生成されるものを含む) では、ATL スタイル .rgs ファイルを使用して、登録情報を格納します。 .Rgs ファイル形式は ATL に固有でありとして一般的に使用することはできません-作成ツールのインストールでは、します。 VSPackage のインストーラーの登録情報は、別々 に保持する必要があります。 たとえば、開発者できますファイル .reg 形式で .rgs との同期ファイルの変更を保持します。 .Reg ファイルは、開発作業用に「regedit」のトピックとマージまたはインストーラーによって消費されることができます。  
  
## <a name="registering-managed-vspackages"></a>マネージ Vspackage を登録します。  
 RegPkg ツールは、マネージ VSPackage から登録属性を読み取り、レジストリまたはインストーラーで使用できる書き込み .reg 形式のファイルに直接情報を書き込むことができますか。  
  
> [!NOTE]
>  RegPkg ツールは、再頒布可能パッケージではありませんし、ユーザーのシステム上の VSPackage の登録に使用することはできません。  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>なぜ Vspackage 登録しないでくださいセルフ インストール時に  
 VSPackage インストーラーには、自己登録に依存する必要があります。 一見すると、VSPackage 自体でのみ、VSPackage のレジストリ値の保持は、ことをお勧めのように見えます。 ある開発者を日常的な作業の使用可能なレジストリ値と、テストすると良い installer で、レジストリ データの個別のコピーを維持してください。 インストーラーは、レジストリ値を書き込んだり自体、VSPackage に利用できます。  
  
 理論的な中に自己登録は VSPackage のインストールには適さないようないくつかの欠点があります。  
  
-   インストール、アンインストール、インストールのロールバック、およびアンインストールのロールバックを正しくサポートするには、RegPkg を呼び出すことにより自己登録するすべてのマネージ VSPackage の 4 つのカスタム アクションを作成する必要があります。  
  
-   サイド バイ サイドのサポート方法では、RegSvr32 または RegPkg をすべてサポートされているバージョンの呼び出しを次の 4 つのカスタム アクションを作成することが必要場合があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
-   自己登録されているモジュールを使用したインストールは、自己登録キーが別の機能またはアプリケーションによって使用されるかどうかに通知する手段がないため安全にロールバックことはできません。  
  
-   自己登録された Dll は、補助 Dll は存在しないか、間違ったバージョンがインストールされている場合がありますにリンクします。 これに対し、Windows インストーラーは、システムの現在の状態に依存せずに、レジストリのテーブルを使用して Dll を登録できます。  
  
-   タイプ ライブラリなどのネットワーク リソースへのアクセス コンポーネントがある場合両方実行元として指定および SelfReg 表に記載されて、自己登録コードを拒否できます。 これにより、管理者用インストール中に失敗するコンポーネントのインストールが発生することができます。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [マネージ パッケージの登録](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)