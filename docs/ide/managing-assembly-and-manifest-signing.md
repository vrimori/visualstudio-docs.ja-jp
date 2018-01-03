---
title: "アセンブリおよびマニフェストへの署名の管理 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d8227a514887150e3477e026a238df608fe98d11
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="managing-assembly-and-manifest-signing"></a>アセンブリおよびマニフェストへの署名の管理
厳密な名前の署名により、ソフトウェア コンポーネントはグローバル一意識別子 (GUID) を付与されます。 厳密な名前を使用すると、別のユーザーによるアセンブリのなりすましが不可能になることが保証され、コンポーネントの依存関係と構成ステートメントが、適切なコンポーネントとコンポーネントのバージョンに確実に対応付けられます。  
  
 厳密な名前は、アセンブリの識別子 (単純テキスト名、バージョン番号、カルチャ情報)、公開キー トークン、およびデジタル署名で構成されます。  
  
 Visual Basic プロジェクトと C# プロジェクトのアセンブリへの署名については、「[厳密な名前付きアセンブリの作成と使用](http://msdn.microsoft.com/Library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9)」を参照してください。  
  
 Visual C++ プロジェクトのアセンブリへの署名については、「[厳密名アセンブリ (アセンブリ署名) (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)」を参照してください。  

> [!NOTE]
>  厳密な名前の署名は、アセンブリのリバース エンジニアリングに対して保護されません。  リバース エンジニアリングに対して保護する方法については、「[Dotfuscator Community Edition (CE)](dotfuscator/index.md)」を参照してください。
  
## <a name="asset-types-and-signing"></a>アセットの型と署名  
 .NET のアセンブリとアプリケーション マニフェストに署名することができます。 次に例を示します。  
  
-   実行可能ファイル (.exe)  
  
-   アプリケーション マニフェスト (.exe.manifest)  
  
-   配置マニフェスト (.application)  
  
-   共有コンポーネント アセンブリ (.dll)  
  
次の種類のアセットに署名する必要があります。  
  
1.  アセンブリ - アセンブリをグローバル アセンブリ キャッシュ (GAC: Global Assembly Cache) に配置する場合。  
  
2.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のアプリケーション マニフェストと配置マニフェスト。 Visual Studio では、これらのアプリケーションに対する署名が既定で有効になります。  
  
3.  COM 相互運用のために使用されるプライマリ相互運用機能アセンブリ。 TLBIMP ユーティリティは、COM タイプ ライブラリからプライマリ相互運用機能アセンブリを作成するときに、厳密な名前付けを強制的に適用します。  
  
一般に、実行可能ファイルに署名する必要はありません。 厳密な名前付きコンポーネントは、アプリケーションと共に配置される、厳密な名前を持たないコンポーネントを参照することはできません。 Visual Studio は、アプリケーションの実行可能ファイルに署名しませんが、厳密な名前を持たない実行可能ファイルを指すアプリケーション マニフェストに署名します。 署名を行うと、依存関係を管理しにくくなります。そのため、一般的に、アプリケーションにとってプライベートなコンポーネントに署名することは避けてください。  
  
## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Visual Studio 内でアセンブリに署名する方法  
 **[署名]** タブを使用してアプリケーションまたはコンポーネントに署名するには、プロジェクトのプロパティ ウィンドウに移動 (**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして **[プロパティ]** をクリックするか、**[クイック起動]** ウィンドウに**プロジェクトのプロパティ**を入力するか、**ソリューション エクスプローラー** ウィンドウ内で Alt キーを押しながら Enter キーを押す) します。 **[署名]** タブを選択し、**[アセンブリの署名]** チェック ボックスをオンにします。  
  
 キー ファイルを指定します。 新しいキー ファイルを作成する場合は、新しいキー ファイルは必ず .pfx ファイル形式で作成されることに注意してください。 新しいファイルの名前とパスワードが必要です。  
  
> [!WARNING]
>  キー ファイルは常にパスワードで保護して、第三者が使用できないようにする必要があります。 プロバイダーまたは証明書ストアを使用して、キーを保護することもできます。  
  
 また、既に作成したキーを指定することもできます。 キーの作成の詳細については、「[方法 : 公開キーと秘密キーのキー ペアを作成する](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)」を参照してください。  
  
 公開キーのみにアクセスできる場合は、遅延署名を使用して、キーの割り当てを遅延させることができます。 **[遅延署名のみ]** チェック ボックスをオンにすると、遅延署名が有効になります。 遅延署名されたプロジェクトは実行されず、デバッグすることもできません。 ただし、[Sn.exe (厳密名ツール)](/dotnet/framework/tools/sn-exe-strong-name-tool) で `-Vr` オプションを指定すると、開発時に検証をスキップできます。  
  
 マニフェストへの署名については、「[方法: アプリケーション マニフェストおよび配置マニフェストに署名する](../ide/how-to-sign-application-and-deployment-manifests.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [厳密な名前付きアセンブリ](/dotnet/framework/app-domains/strong-named-assemblies)   
 [厳密名アセンブリ (アセンブリ署名) (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)