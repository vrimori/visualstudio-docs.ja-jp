---
title: VSPackage の登録 |Microsoft Docs
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
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30da9208df8c5b9b7c3368ef10fc85e55a994baa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782025"
---
# <a name="vspackage-registration"></a>VSPackage の登録
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vspackage に通知する必要があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]読み込めませんがインストールされ、必要があります。 このプロセスは、レジストリの情報を記述することで実施されます。 インストーラーの標準的なジョブです。  
  
> [!NOTE]
>  自己登録を使用する VSPackage 開発時に許容されるです。 ただし、[!INCLUDE[vsipprvsip](../../includes/vsipprvsip-md.md)]パートナーは、セットアップの一環として自己登録を使用して製品を出荷できません。  
  
 Windows インストーラー パッケージのレジストリ エントリは、レジストリの表に一般的に行われます。 レジストリの表にファイル拡張子を登録することもできます。 ただし、Windows インストーラーは、プログラム id (ProgId)、クラス、拡張機能、および動詞テーブルでの組み込みのサポートを提供します。 詳細については、次を参照してください。[データベース テーブル](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)します。  
  
 レジストリ エントリがサイド バイ サイドで選択した戦略に適切なコンポーネントに関連付けられていることを確認します。 たとえば、共有ファイルのレジストリ エントリはそのファイルの Windows インストーラー コンポーネントに関連付けられてになります。 同様に、バージョン固有のファイルのレジストリ エントリは、そのファイルのコンポーネントに関連付けられてする必要があります。 それ以外の場合、インストールまたはの 1 つのバージョンについては、VSPackage のアンインストール[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]他のバージョンで、VSPackage を中断する可能性があります。 詳細については、次を参照してください[をサポートしている複数のバージョンの Visual Studio。](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  登録を管理する最も簡単な方法は、開発者の登録とインストール時の登録の両方に同じファイルで同じデータを使用します。 たとえば、一部のインストーラー開発ツールでは、ビルド時に .reg 形式のファイルを使用できます。 開発者が独自の日常的な開発のための .reg ファイルを維持し、デバッグ、それらのファイルに含めることできますインストーラーに自動的にします。 場合、 登録データを自動的に共有することはできない場合は、登録データのインストーラーのコピーが最新であることを確認する必要があります。  
  
## <a name="registering-unmanaged-vspackages"></a>アンマネージ Vspackage の登録  
 アンマネージ Vspackage を (Visual Studio パッケージ テンプレートによって生成されたものを含む) では、ATL スタイル .rgs ファイルを使用して、登録情報を格納します。 .Rgs ファイルの形式は ATL に固有ととして一般的に使用することはできません-作成ツールをインストールすることです。 VSPackage のインストーラーの登録情報を別々 に保持する必要があります。 たとえば、開発者できますファイル .reg 形式で .rgs との同期ファイルの変更を保持します。 .Reg ファイルを RegEdit 開発作業をマージまたはインストーラーによって消費されることができます。  
  
## <a name="registering-managed-vspackages"></a>マネージ Vspackage を登録します。  
 RegPkg ツールは、マネージ VSPackage から登録属性を読み取るし、インストーラーで使用できる書き込み .reg 形式のファイル、レジストリに直接情報を書き込むことができますか。  
  
> [!NOTE]
>  RegPkg ツールは、再頒布可能パッケージでないし、ユーザーのシステム上の VSPackage の登録に使用することはできません。  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>なぜ Vspackage は自己登録インストール時に  
 VSPackage、インストーラーは、自己登録に依存する必要があります。 一見、それ自体、VSPackage でのみ VSPackage のレジストリ値を維持する方法をお勧めのように見えます。 ある開発者が日常的な仕事の使用可能なレジストリ値を必要し、テスト、理にかなってインストーラーのレジストリ データの個別のコピーを維持してください。 インストーラーは、レジストリ値を書き込んだり自体を VSPackage に利用できます。  
  
 理論上は適切です、自己登録は VSPackage のインストールには適さないするいくつかの欠点があります。  
  
-   インストール、アンインストール、インストールのロールバック、およびアンインストールのロールバックを正しくサポートするには、RegPkg を呼び出して自己登録するすべてのマネージ VSPackage の 4 つのカスタム アクションを作成する必要があります。  
  
-   サイド バイ サイドでサポートするアプローチがサポートされているどのバージョンの RegSvr32 または RegPkg を呼び出す次の 4 つのカスタム アクションを作成する必要があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
-   自己登録済みモジュールのインストールは、自己登録キーが別の機能またはアプリケーションによって使用されるかどうかに通知する手段がないために戻す安全にロールバックできません。  
  
-   補助の Dll は存在しないか、間違ったバージョンがも自己登録済みの Dll にリンクします。 これに対し、Windows インストーラーは、システムの現在の状態に依存せずに、レジストリのテーブルを使用して Dll を登録できます。  
  
-   タイプ ライブラリなどのネットワーク リソースへのアクセス コンポーネントがある場合ソースからの実行として指定し、SelfReg テーブルに格納されて、自己登録コードを拒否できます。 管理者用インストールが失敗するコンポーネントのインストールがある可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Managed Package の登録](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

