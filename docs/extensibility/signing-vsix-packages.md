---
title: "VSIX パッケージに署名する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 12
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
ms.openlocfilehash: da489f0fd0483cddbefb2899eb91bd1d56735d62
ms.lasthandoff: 02/22/2017

---
# <a name="signing-vsix-packages"></a>VSIX パッケージに署名します。
拡張機能アセンブリは、Visual Studio で実行できますが、これを行うことをお勧めする前に署名する必要はありません。  
  
 拡張機能をセキュリティで保護し、改ざんされていないことを確認する場合は、VSIX パッケージにデジタル署名を追加できます。 VSIX は、署名済み、VSIX インストーラーによって、署名があるの詳細については、署名自体を加えたことを示すメッセージが表示されます。 VSIX のコンテンツが変更されて、VSIX に再度署名されていない場合は、署名が無効である VSIX インストーラーが表示されます。 インストールが停止していないが、ユーザーに警告が表示されます。  
  
> [!IMPORTANT]
>  2015 以降では、VSIX パッケージには SHA256 暗号化以外のものを使用して署名が無効な署名を持つとして識別されます。 VSIX のインストールはブロックされませんが、ユーザーに警告が表示されます。  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>VSIXSignTool で VSIX の署名  
 署名ツールから利用可能には SHA256 暗号化されることは[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)で nuget.org で[VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)します。  
  
#### <a name="to-use-the-vsixsigntool"></a>VSIXSignTool を使用するには  
  
1.  プロジェクトに、VSIX を追加します。  
  
2.  ソリューション エクスプ ローラーでプロジェクト ノードを右クリックを選択すると**追加 |NuGet パッケージの管理**します。  詳細については、NuGet を追加して NuGet パッケージを参照してください[NuGet 概要](http://docs.nuget.org/)と[NuGet パッケージを使用して管理ダイアログ](http://docs.nuget.org/Consume/Package-Manager-Dialog)します。  
  
3.  VSIXSignTool VisualStudioExtensibility から検索し、NuGet パッケージをインストールします。  
  
4.  プロジェクトのローカル パッケージの場所から、VSIXSignTool を実行できます。 署名のシナリオでは、ツールのコマンド ライン ヘルプを参照してください (VSIXSignTool.exe/?)。  
  
 たとえば、パスワード保護されている証明書ファイルを使用して署名します。  
  
 VSIXSignTool.exe 記号/f \<certfile >/p\<パスワード > \<VSIXfile >  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)
