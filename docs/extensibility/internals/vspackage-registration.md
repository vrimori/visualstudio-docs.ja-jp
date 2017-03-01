---
title: "VSPackage 登録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bebd023d8cbecf97f75570bf57ed2cd4462ffe92
ms.lasthandoff: 02/22/2017

---
# <a name="vspackage-registration"></a>VSPackage の登録
VSPackages にアドバイスする必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]読み込めますがインストールされ、必要があります。 このプロセスは、情報をレジストリに書き込むことで実行します。 インストーラーの一般的なジョブです。  
  
> [!NOTE]
>  開発時に VSPackage に自己登録を使用してが許容されるです。 ただし、[!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)]パートナーは、セットアップの一部として自己登録を使用して製品を提供できません。  
  
 Windows インストーラー パッケージのレジストリ エントリは、レジストリの表に一般的に行われます。 レジストリの表に、ファイル拡張子を登録することもできます。 ただし、Windows インストーラーは、プログラム id (ProgId)、クラス、拡張機能、および動詞テーブルからの組み込みサポートを提供します。 詳細については、次を参照してください。[データベース テーブル](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx)します。  
  
 レジストリ エントリは、選択したサイド バイ サイド戦略に適したコンポーネントに関連付けられていることを確認します。 たとえば、共有ファイルのレジストリ エントリは、そのファイルの Windows インストーラーのコンポーネントに関連付けられてする必要があります。 同様に、バージョン固有のファイルのレジストリ エントリは、そのファイルのコンポーネントを関連付ける必要があります。 それ以外の場合、インストールまたはの&1; つのバージョンについては、VSPackage をアンインストール[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]他のバージョンで、VSPackage を中断する可能性があります。 詳細については、次を参照してください[をサポートする複数のバージョンの Visual Studio。](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  登録を管理する最も簡単な方法では、開発者の登録と登録のインストール時の両方に同じファイルで同じデータを使用します。 たとえば、いくつかのインストーラーの開発ツールでは、ビルド時に .reg 形式のファイルを使用できます。 開発者が独自の日常的な開発用の .reg ファイルを管理すると、デバッグ、それらのファイルに含まれるインストーラー自動的にします。 登録データを自動的に共有することはできない場合は、登録データのインストーラーのコピーが現在であることを確認する必要があります。  
  
## <a name="registering-unmanaged-vspackages"></a>アンマネージ VSPackages を登録します。  
 アンマネージ vspackages にある (Visual Studio パッケージ テンプレートによって生成されたものを含む) では、ATL スタイル .rgs ファイルを使用して、登録情報を格納します。 .Rgs ファイル形式は、ATL を特定しとして一般的に使用できません-作成ツールのインストールによってです。 VSPackage インストーラーの登録情報を個別に保持する必要があります。 たとえば、開発者できますファイル .reg 形式での同期を維持 .rgs ファイルの変更。 .Reg ファイルは、開発作業に「regedit」のトピックとマージまたはインストーラーによって消費されることができます。  
  
## <a name="registering-managed-vspackages"></a>マネージ VSPackages を登録します。  
 RegPkg ツールは、マネージ VSPackage から登録属性を読み取り、レジストリまたはインストーラーから消費可能な書き込み .reg 形式のファイルに直接、情報を書き込むことができますか。  
  
> [!NOTE]
>  RegPkg ツールでは、再頒布可能パッケージではなく、ユーザーのシステム上の VSPackage の登録に使用することはできません。  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>なぜ vspackages にある登録しないでください自己インストール時に  
 VSPackage インストーラーは、自己登録に依存する必要があります。 一見、VSPackage 自体でのみ VSPackage のレジストリの値の保持をお勧めのように見えます。 開発者は、日常的な作業の使用可能なレジストリ値を必要、テスト、合理的にインストーラーのレジストリ データのコピーを個別に維持してください。 インストーラーは、レジストリ値を書き込むには、VSPackage 自体に利用できます。  
  
 理論上は適切です、自己登録は VSPackage インストール不適切なことがいくつかの欠点があります。  
  
-   インストール、アンインストール、インストールのロールバック、およびアンインストールのロールバックを正しくサポートするには、RegPkg の呼び出しを自己登録するすべてのマネージ VSPackage の&4; つのカスタム アクションを作成する必要があります。  
  
-   サイド バイ サイドのサポートのアプローチがサポートされているどのバージョンの RegSvr32 または RegPkg を呼び出す次の&4; つのカスタム アクションを作成する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
-   自己登録されているモジュールを使用したインストールは、自己登録キーが別の機能またはアプリケーションによって使用されるかどうかに通知する手段がないとしているため安全にロールバックできません。  
  
-   補助 Dll が存在しないか、不適切なバージョンをも自己登録されている Dll にリンクします。 これに対し、Windows インストーラーは、システムの現在の状態に依存せずに、レジストリのテーブルを使用して Dll を登録できます。  
  
-   自己登録コードは、タイプ ライブラリなどのネットワーク リソースへのアクセス コンポーネントがある場合両方として指定ソースから実行され、SelfReg の表に示す拒否できます。 管理者用インストールに支障をきたしますコンポーネントのインストールがある可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラー](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [管理されているパッケージの登録](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
