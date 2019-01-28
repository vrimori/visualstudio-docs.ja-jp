---
title: CA5351 破られた暗号アルゴリズムを使用しないでください
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab965c8912144350c527517b79de2914e238976e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037721"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 破られた暗号アルゴリズムを使用しないでください

|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|カテゴリ|Microsoft.Cryptography|
|互換性に影響する変更点|中断なし|

> [!NOTE]
> この警告の最終更新は 2015 年 11 月です。

## <a name="cause"></a>原因

<xref:System.Security.Cryptography.MD5> などのハッシュ関数および <xref:System.Security.Cryptography.DES> や <xref:System.Security.Cryptography.RC2> などの暗号アルゴリズムは、重大な危険にさらされている可能性があり、ブルート フォース攻撃やハッシュの競合など、単純な攻撃方法を通して機密情報が漏洩する可能性があります。

下の暗号アルゴリズムの一覧は、既知の暗号攻撃を受ける可能性があります。 暗号化ハッシュ アルゴリズム <xref:System.Security.Cryptography.MD5> は、ハッシュの競合攻撃を受ける可能性があります。  使用状況に応じて、ハッシュの競合は、偽装、改ざん、またはハッシュ関数の一意の暗号出力を使用するシステムへのその他の種類の攻撃を招く可能性があります。 暗号アルゴリズム <xref:System.Security.Cryptography.DES> と <xref:System.Security.Cryptography.RC2> は、暗号化されたデータの意図しない漏洩につながる可能性のある暗号攻撃の対象となる可能性があります。

## <a name="rule-description"></a>規則の説明

破られた暗号アルゴリズムはセキュアであるとは見なされず、それらを使用しないことをお勧めします。 使用コンテキストに応じて特定の脆弱性は異なりますが、MD5 ハッシュ アルゴリズムは既知の競合攻撃の影響を受けやすくなっています。  (たとえば、ファイルの署名またはデジタル証明書) のデータ整合性を確保するために使用するハッシュ アルゴリズムは、特に脆弱です。  このコンテキストでは、攻撃者が 2 つの独立したデータを生成し、ハッシュ値を変更したり、関連付けられているデジタル署名を無効にしたりすることなく、悪意のないデータを悪意のあるデータで置き換えるなどの可能性があります。

暗号アルゴリズムの場合:

- <xref:System.Security.Cryptography.DES> 暗号のキー サイズは小さく、1 日未満でブルートフォースが実行される可能性があります。

- <xref:System.Security.Cryptography.RC2> 暗号は、攻撃者がすべてのキー値の間の数学的な関係を検出する関連鍵攻撃の影響を受けやすくなっています。

この規則は、ソース コードに上記の暗号化関数のいずれかが見つかり、ユーザーに警告をスローする場合にトリガーされます。

## <a name="how-to-fix-violations"></a>違反の修正方法

暗号強度の高いオプションを使用します。

- MD5 ハッシュを使用、 [sha-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms)ファミリ (たとえば、 <xref:System.Security.Cryptography.SHA512>、 <xref:System.Security.Cryptography.SHA384>、 <xref:System.Security.Cryptography.SHA256>)。

- DES と RC2 の場合は、 <xref:System.Security.Cryptography.Aes> 暗号を使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

暗号の専門家によって確認された場合を除き、この規則からの警告を抑制しないでください。

## <a name="pseudo-code-examples"></a>疑似コードの例

次の擬似コード サンプルでは、この規則や考えによって検出されたパターンを示しています。

### <a name="md5-hashing-violation"></a>MD5 ハッシュ違反

```csharp
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();
```

解決方法 : 

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="rc2-encryption-violation"></a>RC2 暗号化違反

```csharp
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();
```

解決方法 : 

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```

### <a name="des-encryption-violation"></a>DES 暗号化違反

```csharp
using System.Security.Cryptography;
...
DES encAlg = DES.Create();
```

解決方法 : 

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```