# PKI Subordinate CPS

<table>
    <tr>
      <td  valign="top"><h2> 6.  TECHNICAL SECURITY CONTROLS</h2></td>
      <td  valign="top">Related Requirements</td>
      </tr>
   <tr>
      <td  valign="top">Technical security controls are defined in accordance with [ETSI EN 319 411-1] and [ETSI EN 319 401]. The technical security controls address:
      <ul>
        <li>the security measures taken by the Siemens CA to protect its Root Key Pairs and Activation Data (e.g. passwords)</li>
        <li>other technical security controls used to perform securely the functions listed in CP § 1.1, including technical controls such as life-cycle security controls (e.g., software development environment security, trusted softwaredevelopment methodology) and operational security controls.</li>
    </ul>
      </td>
      <td  valign="top"><b>RFC</b>  <br>4.6 Technical Security Controls  <br> <br>This component is used to define the security measures taken by the issuing CA to protect its cryptographic keys and activation data (e.g., PINs, passwords, or manually-held key shares).  This component may also be used to impose constraints on repositories, subject CAs, subscribers, and other participants to protect their private keys, activation data for their private keys, and critical security parameters.  Secure key management is critical to ensure that all secret and private keys and activation data are protected and used only by authorized personnel.  <br> <br>This component also describes other technical security controls used by the issuing CA to perform securely the functions of key generation, user authentication, certificate registration, certificate revocation, auditing, and archiving.  Technical controls include life-cycle security controls (including software development environment security, trusted software development methodology) and operational security controls.  <br> <br>This component can also be used to define other technical security controls on repositories, subject CAs, RAs, subscribers, and other participants.<br><br><b>BRG</b>  <br>Empty<br><br><b>ETSI EN 319 401 V2.2.1</b> <br><br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h3>6.1  Key pair generation and installation</h3></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top"><b>RFC</b><br>4.6.1.  Key Pair Generation and Installation<br> <br> Key pair generation and installation need to be considered for the issuing CA, repositories, subject CAs, RAs, and subscribers.  For  each of these types of entities, the following questions potentially need to be answered:
      <ol>
        <li>Who generates the entity public, private key pair?  Possibilities include the subscriber, RA, or CA.  Also, how is the key generation performed?  Is the key generation performed by hardware or software?</li>
        <li>How is the private key provided securely to the entity? Possibilities include a situation where the entity has generated it and therefore already has it, handing the entity the private key physically, mailing a token containing the private key securely, or delivering it in an SSL session.</li>
        <li>How is the entity's public key provided securely to the certification authority?  Some possibilities are in an online SSL session or in a message signed by the RA.</li>
        <li>In the case of issuing CAs, how is the CA's public key provided securely to potential relying parties?  Possibilities include handing the public key to the relying party securely in person, physically mailing a copy securely to the relying party, or delivering it in a SSL session.</li>
        <li>What are the key sizes?  Examples include a 1,024 bit RSA modulus and a 1,024 bit DSA large prime.</li>
        <li>Who generates the public key parameters, and is the quality of the parameters checked during key generation?</li>
        <li>For what purposes may the key be used, or for what purposes should usage of the key be restricted?  For X.509 certificates, these purposes should map to the key usage flags in X.509 Version 3 certificates.</li>
      </ol>
      <b>BRG</b>  <br> Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br> 7.5 Cryptographic controls<br> <br> REQ-7.5-01: Appropriate security controls shall be in place for the management of any cryptographic keys and any cryptographic devices throughout their lifecycle. NOTE: See clause 10 of ISO/IEC 27002:2013 [i.3] for guidance.<br>  <br><b>ETSI EN 319 411-1 V1.2.1</b><br> 6.5.1 Key pair generation and installation<br> <br> OVR-6.5.1-01: The requirements identified in ETSI EN 319 401 [8], clause 7.5, shall apply.<br> <br> In addition the following particular requirements apply:<br> <br> GEN-6.5.1-02: The TSP shall generate CA keys, including keys used by revocation and registration services, securely and the private key shall be secret.<br>In particular:
      <ul>
        <li>GEN-6.5.1-03: The CA key pair generation and the subsequent certification of the public key, shall be undertaken in a physically secured environment (see clause 6.4.2) by personnel in trusted roles (see clause 6.4.4).</li>
        <li>GEN-6.5.1-04: The CA key pair used for signing certificates shall be created under, at least, dual control.</li>
        <li>GEN-6.5.1-05: The number of personnel authorized to carry out CA key pair generation shall be kept to a minimum and be consistent with the TSP's practices.</li>
        <li>GEN-6.5.1-06: CA key pair generation should be performed using an algorithm as specified in ETSI TS 119 312 [i.10] for the CA's signing purposes. NOTE 1: Cryptographic suites recommendations defined in ETSI TS 119 312 [i.10] can be superseded by national recommendations.</li>
        <li>GEN-6.5.1-07: The selected key length and algorithm for CA signing key should be one which is specified in ETSI TS 119 312 [i.10] for the CA's signing purposes. NOTE 2: Cryptographic suites recommendations defined in ETSI TS 119 312 [i.10] can be superseded by national recommendations.</li>
        <li>GEN-6.5.1-08: Before expiration of its CA certificate which is used for signing subject keys (for example as indicated by expiration of CA certificate), in case of continuing with the service, the CA shall generate a new certificate for signing subject key pairs, and shall apply all necessary actions to avoid disruption to the operations of any entity that may rely on the CA certificate.</li>
        <li>GEN-6.5.1-09: Before expiration of its CA certificate which is used for signing subject keys (for example as indicated by expiration of CA certificate), in case of continuing with the service, the new CA certificate shall also be generated and distributed in accordance with the present document.
      </ul>
        GEN-6.5.1-10: The operations described in GEN-6.5.1-08 and GEN-6.5.1-09 should be performed with a suitable interval between certificate expiry date and the last certificate signed to allow all parties that have relationships with the TSP (subjects, subscribers, relying parties, CAs higher in the CA hierarchy, etc.) to be aware of this key changeover and to implement the required operations to avoid inconveniences and malfunctions. This does not apply to a TSP which will cease its operations before its own certificate-signing certificate expiration date.<br> <br>
        GEN-6.5.1-11: The TSP shall have a documented procedure for conducting CA key pair generation for certificate signing keys for all CAs, whether root CAs or subordinate CAs, including CAs that issue certificates to end users.<br> <br>
        GEN-6.5.1-12: The procedure of GEN-6.5.1-11 shall indicate, at least, the following:
        <ol  type="a">
          <li>roles participating in the ceremony (internal and external from the organization);</li>
          <li>functions to be performed by every role and in which phases;</li>
          <li>responsibilities during and after the ceremony; and</li>
          <li>requirements of evidence to be collected of the ceremony.</li>
        </ol>
        
        GEN-6.5.1-13: The TSP shall produce a report proving that the ceremony, as in GEN-6.5.1-11 above, was carried out in accordance with the stated procedure and that the integrity and confidentiality of the key pair was ensured.<br> <br>
        GEN-6.5.1-14: This report shall be signed [CHOICE]:
        <ul>
          <li>For root CA: by the trusted role responsible for the security of the TSP's key management ceremony (e.g. security officer) and a trustworthy person independent of the TSP's management (e.g. Notary, auditor) as<br>witness that the report correctly records the key management ceremony as carried out.</li>
          <li>For subordinate CAs: by the trusted role responsible for the security of the TSP's key management ceremony (e.g. security officer) as witness that the report correctly records the key management ceremony as carried out.</li>
        </ul>
          GEN-6.5.1-15 [PTC]: Clause 6.1.1.1 of the BRG [5] shall apply.<br> <br>
          DIS-6.5.1-16: CA signature verification (public) keys shall be available to relying parties in a manner that assures the integrity of the CA public key and authenticates its origin.<br> <br> NOTE 3: For example, CA public keys can be distributed in self-signed certificates, along with a declaration that the key authenticates the CA, or issued by another CA. By itself a self-signed certificate cannot be known to come from the CA. Additional measures, such as checking the fingerprint of the certificate against information provided by a trusted source, is needed to give assurance of the correctness of this certificate.<br> <br>
          When the CA generates the subject's keys:
          <ul>
            <li> SDP-6.5.1-17 [CONDITIONAL]: If the CA generates the subject's keys, CA-generated subject keys shall be generated using an algorithm recognized as being fit for the uses identified in the CP during the validity time of the certificate.</li>
            <li>SDP-6.5.1-18 [CONDITIONAL]: If the CA generates the subject's keys, CA-generated subject keys should be of a key length and for use with a public key algorithm as specified in ETSI TS 119 312 [i.10] for the purposes stated in the CP during the validity time of the certificate. NOTE 4: Cryptographic suites recommendations defined in ETSI TS 119 312 [i.10] can be superseded by national recommendations.</li>
            <li>SDP-6.5.1-19 [CONDITIONAL]: If the CA generates the subject's keys , CA-generated subject keys shall be generated and stored securely whilst held by the TSP.</li>
            <li>SDP-6.5.1-20 [CONDITIONAL]: If the CA generates the subject's keys, the subject's private key shall be delivered to the subject's device or to the TSP managing the subject's private key, in a manner such that the secrecy and integrity of the key is not compromised.</li>
            <li>SDP-6.5.1-21 [CONDITIONAL]: If the CA generates the subject's keys and if the TSP or any of its designated RAs become aware that a subject's private key has been communicated to an unauthorized person or an organization not affiliated with the subject, then the TSP shall revoke all certificates that include the public key corresponding to the communicated private key.</li>
            <li>SDP-6.5.1-22 [CONDITIONAL]: If the CA generates the subject's keys, the CA shall delete all copies of a subject private key after delivery of the private key to the subject, except for conditions as described in clause 6.3.12.</li>
            <li>SDP-6.5.1-23 [NCP+] [CONDITIONAL]: If the CA generates the subject's keys, the TSP shall secure the issuance of a secure cryptographic device to the subject.</li>
          </ul>
          In particular:
          <ul>
            <li>SDP-6.5.1-24 [CONDITIONAL]: If the CA generates the subject's keys, secure cryptographic device preparation shall be done securely.</li>
            <li>SDP-6.5.1-25 [CONDITIONAL]: If the CA generates the subject's keys, secure cryptographic device shall be securely stored and distributed.</li>
          </ul>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.1.1  Key pair generation</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty)</td>
      <td  valign="top"><b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>  See chapter 6.1<br>  <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   See chapter 6.1<br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h5>6.1.1.1 CA Key Pair Generation</h5> </td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">The Key Pairs of the Root CAs and Issuing CAs are generated  are generated pursuant to formal key generation procedures and inside of a hardware security module (“HSM”), which is certified in accordance with FIPS 140-2 Level 3. All operations that involve the CA keys are performed under dual control by trusted roles in the physiscally secured environment of the Eagle DC and documented according the requirements set forth in the CA and HSM Management | 3.2 Rollenverteilung bei CA Events</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   For Root CA Key Pairs created after the Effective Date that are either (i) used as Root CA Key Pairs or (ii) Key Pairs generated for a subordinate CA that is not the operator of the Root CA or an Affiliate of the Root CA, the CA SHALL:
    <ol>
      <li>prepare and follow a Key Generation Script,</li>
      <li>have a Qualified Auditor witness the Root CA Key Pair generation process or record a video of the entire Root CA Key Pair generation process, and</li>
      <li>have a Qualified Auditor issue a report opining that the CA followed its key ceremony during its Key and Certificate generation process and the controls used to ensure the integrity and confidentiality of the Key Pair.</li>
    </ol>
      For other CA Key Pairs created after the Effective Date that are for the operator of the Root CA or an Affiliate of the Root CA, the CA SHOULD:
    <ol>
      <li>prepare and follow a Key Generation Script and </li>
      <li>have a Qualified Auditor witness the Root CA Key Pair generation process or record a video of the entire Root CA Key Pair generation process.</li>
    </ol>
     In all cases, the CA SHALL:
    <ol>
     <li>generate the keys in a physically secured environment as described in the CA's Certificate Policy and/or Certification Practice Statement;</li>
     <li>generate the CA keys using personnel in Trusted Roles under the principles of multiple person control and split knowledge;</li>
     <li>generate the CA keys within cryptographic modules meeting the applicable technical and business requirements as disclosed in the CA's Certificate Policy and/or Certification Practice Statement;</li>
     <li>log its CA key generation activities; and</li>
     <li>maintain effective controls to provide reasonable assurance that the Private Key was generated and protected in conformance with the procedures described in its Certificate Policy and/or Certification Practice Statement and (if applicable) its Key Generation Script.</li>
    </ol>
    <br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>  See chapter 6.1<br>  <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   See chapter 6.1<br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h5> 6.1.1.2 RA Key Pair Generation</h5></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>  See chapter 6.1<br>  <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   See chapter 6.1<br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h5> 6.1.1.3 Subscriber Key Pair Generation</h5></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Requests for Subscriber Certificates are rejected if the Public Key does not meet the requirements set forth in Sections 6.1.5 and 6.1.6 or if it has a known weak Private Key.
      </td>
    <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   The CA SHALL reject a certificate request if the requested Public Key does not meet the requirements set forth in Sections 6.1.5 and 6.1.6 or if it has a known weak Private Key (such as a Debian weak key, see http://wiki.debian.org/SSLkeys).<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>  See chapter 6.1<br>  <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   See chapter 6.1<br>
    </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.1.2  Private key delivery to subscriber</h4> </td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">During the operation of the Siemens Issuing CAs, the trusted operator ensures that the CAs’ Private Key do not leave its secure facility.<br><br>For certifcates related to natural persons or to servers, details are described in the CPS Natural Persons Related Certificates, CPS TLS/SSL resp.<br><br>As soon as the CA is being informed via ServerRA notification that a private key has been compromised all corresponding certificates are being revoked..<br><br>
      </td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   Parties other than the Subscriber SHALL NOT archive the Subscriber Private Key without authorization by the Subscriber.<br> <br> If the CA or any of its designated RAs generated the Private Key on behalf of the Subscriber, then the CA SHALL encrypt the Private Key for transport to the Subscriber.<br> <br> If the CA or any of its designated RAs become aware that a Subscriber's Private Key has been communicated to an unauthorized person or an organization not affiliated with the Subscriber, then the CA SHALL revoke all certificates that include the Public Key corresponding to the communicated Private Key.<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.1.3  Public key delivery to certificate issuer</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Compare chapter 4.4.2.
      </td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.1.4  CA public key delivery to relying parties</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Compare CP, chapter 6.1.4 .<br><br>
      </td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.1.5  Key sizes</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">The algorithms, parameters and key sizes used by Siemens CA are defined in the Certificate Profile document available on www.siemens.com/pki based on the recommendations of ETSI TS 119 312.<br><br>All EE certificates are generated with a minimum key size of 2.048 Bits. They are all signed with SHA-256. Details are described in the End Entity Policy.
      </td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   Certificates MUST meet the following requirements for algorithm type and key size.<br> <br>
      
      (1) Root CA Certificates<br> <br> <br>
      
      <table>
        <tr>
          <th></th>
          <th>Validity period beginning on or before 31 Dec 2010</th>
          <th>Validity period beginning after 31 Dec 2010</th>
        </tr>
        <tr>
          <td>Digest algorithm</td>
          <td>MD5 (NOT RECOMMENDED), SHA-1, SHA-256, SHA-384 or SHA-512</td>
          <td>SHA-1*, SHA-256, SHA-384 or SHA-512</td>
        </tr>
        <tr>
          <td>Minimum RSA modulus size (bits)</td>
          <td>2048**</td>
          <td>2048</td>
        </tr>
        <tr>
          <td>ECC curve</td>
          <td>NIST P-256, P-384, or P-521</td>
          <td>NIST P-256, P-384, or P-521</td>
        </tr>
        <tr>
          <td>Minimum DSA modulus and divisor size (bits)***</td>
          <td>L= 2048 N= 224 or L= 2048 N= 256</td>
          <td>L= 2048 N= 224 or L= 2048 N= 256</td>
        </tr>
      </table>
      
      (2) Subordinate CA Certificates<br> <br>
      
      <table>
        <tr>
          <th></th>
          <th>Validity period beginning on or before 31 Dec 2010 and ending on or before 31 Dec 2013</th>
          <th>Validity period beginning after 31 Dec 2010 or ending after 31 Dec 2013</th>
        </tr>
        <tr>
          <td>Digest algorithm</td>
          <td>SHA-1, SHA-256, SHA-384 or SHA-512</td>
          <td>SHA-1*, SHA-256, SHA-384 or SHA-512</td>
        </tr>
        <tr>
          <td>Minimum RSA modulus size (bits)</td>
          <td>1024</td>
          <td>2048</td>
        </tr>
        <tr>
          <td>ECC curve</td>
          <td>NIST P-256, P-384, or P-521</td>
          <td>NIST P-256, P-384, or P-521</td>
        </tr>
        <tr>
          <td>Minimum DSA modulus and divisor size (bits)***</td>
          <td>L= 2048, N= 224 or L= 2048, N= 256</td>
          <td>L= 2048 N= 224 or L= 2048 N= 256</td>
        </tr>
      </table>
      
      
       (3) Subscriber Certificates<br> <br>
       
       <table>
        <tr>
          <th></th>
          <th>Validity period ending on or before 31 Dec 2013</th>
          <th>Validity period ending after 31 Dec 2013</th>
        </tr>
        <tr>
          <td>Digest algorithm</td>
          <td>SHA1*, SHA-256, SHA-384 or SHA-512</td>
          <td>SHA-1*, SHA-256, SHA-384 or SHA-512</td>
        </tr>
        <tr>
          <td>Minimum RSA modulus size (bits)</td>
          <td>1024</td>
          <td>2048</td>
        </tr>
        <tr>
          <td>ECC curve</td>
          <td>NIST P-256, P-384, or P-521</td>
          <td>NIST P-256, P-384, or P-521</td>
        </tr>
        <tr>
          <td>Minimum DSA modulus and divisor size (bits)</td>
          <td>L= 2048, N= 224 or L= 2048, N= 256</td>
          <td>L= 2048 N= 224 or L= 2048 N= 256</td>
        </tr>
      </table>
       
       
       |<br> <br> * SHA-1 MAY be used with RSA keys in accordance with the criteria defined in Section 7.1.3.<br> <br> ** A Root CA Certificate issued prior to 31 Dec. 2010 with an RSA key size less than 2048 bits MAY still serve as a trust anchor for Subscriber Certificates issued in accordance with these Requirements.<br> <br> *** L and N (the bit lengths of modulus p and divisor q, respectively) are described in the Digital Signature Standard, FIPS 186-4 (http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.186-4.pdf).<br><br>
       <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.1.6  Public key parameters generation and quality checking</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">For RSA keys, the CA confirms that the value of the public exponent is an odd number equal to 3 or more. Additionally, the public exponent is in the range between 216+1 and 2256-1. The modulus has the following characteristics: an odd number, not the power of a prime, and have no factors smaller than 752. <br><br>While issuing a certificate the Public Key is checked against know weaknesses like ROCA oder Debian Weak Key.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   RSA: The CA SHALL confirm that the value of the public exponent is an odd number equal to 3 or more. Additionally, the public exponent SHOULD be in the range between 216+1 and 2256-1. The modulus SHOULD also have the following characteristics: an odd number, not the power of a prime, and have no factors smaller than 752. [Source: Section 5.3.3, NIST SP 800-89]<br> <br> DSA: Although FIPS 800-57 says that domain parameters may be made available at some accessible site, compliant DSA certificates MUST include all domain parameters. This is to insure maximum interoperability among relying party software. The CA MUST confirm that the value of the public key has the unique correct representation and range in the field, and that the key has the correct order in the subgroup. [Source: Section 5.3.1, NIST SP 800-89]<br> <br> ECC: The CA SHOULD confirm the validity of all keys using either the ECC Full Public Key Validation Routine or the ECC Partial Public Key Validation Routine. [Source: Sections 5.6.2.3.2 and 5.6.2.3.3, respectively, of NIST SP 800-56A: Revision 2]<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.1.7  Key usage purposes (as per X.509 v3 key usage field)</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">“KeyUsage” extension fields of Siemens CA Certificates are specified in accordance RFC 5280 and defined in the Certificate Profile document available on www.siemens.com/pki based on the recommendations of ETSI TS 119 312. <br><br>Private Keys corresponding to Root Certificates of the Root CA are only used in the case of  self-signed Certificates to represent the Root CA itself, and for Certificates for Issuing CAs and Cross Certificates;
</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.1<br>  <br><b>BRG</b>  <br>   Private Keys corresponding to Root Certificates MUST NOT be used to sign Certificates except in the following cases:
      <ul>
        <li>Self-signed Certificates to represent the Root CA itself;</li>
        <li>Certificates for Subordinate CAs and Cross Certificates;</li>
        <li>Certificates for infrastructure purposes (administrative role certificates, internal CA operational device certificates); and</li>
        <li>Certificates for OCSP Response verification.</li>
      </ul>
      <b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h3> 6.2  Private Key Protection and Cryptographic Module Engineering Controls</h3></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Certification authority key generation is being undertaken in a physically secured environment by personnel in trusted roles under, at least, dual control. The number of personnel authorized to carry out this function is being kept to a minimum and consistent with the CA's practices. <br><br>CA key generation is being carried out within a device which meets the requirements identified in FIPS PUB 140-1 [2], or FIPS PUB 140-2 [3] level 3 or higher.</td>
      <td  valign="top">  <b>RFC</b>  <br>4.6.2.  Private Key Protection and Cryptographic Module Engineering Controls<br> <br> Requirements for private key protection and cryptographic modules need to be considered for the issuing CA, repositories, subject CAs, RAs, and subscribers.  For each of these types of entities, the following questions potentially need to be answered:
      <ol>
        <li>What standards, if any, are required for the cryptographic module used to generate the keys?  A cryptographic module can be composed of hardware, software, firmware, or any combination of them.  For example, are the keys certified by the infrastructure required to be generated using modules compliant with the US FIPS 140-1?  If so, what is the required FIPS 140-1 level of the module?  Are there any other engineering or other controls relating to a cryptographic module, such as the identification of the cryptographic module boundary, input/output, roles and services, finite state machine, physical security, software security, operating system security, algorithm compliance, electromagnetic compatibility, and self tests.</li>
        <li>Is the private key under n out of m multi-person control?(7)  If yes, provide n and m (two person control is a special case of n out of m, where n = m = 2)?</li>
        <li>Is the private key escrowed?(8)  If so, who is the escrow agent, what form is the key escrowed in (examples include plaintext, encrypted, split key), and what are the security controls on the escrow system?</li>
        <li>Is the private key backed up?  If so, who is the backup agent, what form is the key backed up in (examples include plaintext, encrypted, split key), and what are the security controls on the backup system?</li>
        <li>Is the private key archived?  If so, who is the archival agent, what form is the key archived in (examples include plaintext, encrypted, split key), and what are the security controls on the archival system?</li>
        <li>Under what circumstances, if any, can a private key be transferred into or from a cryptographic module?  Who is permitted to perform such a transfer operation?  In what form is the private key during the transfer (i.e., plaintext, encrypted, or split key)?</li>
        <li>How is the private key stored in the module (i.e., plaintext, encrypted, or split key)?</li>
        <li>Who can activate (use) the private key?  What actions must be performed to activate the private key (e.g., login, power on, supply PIN, insert token/key, automatic, etc.)?  Once the key is activated, is the key active for an indefinite period, active for one time, or active for a defined time period?</li>
        <li>Who can deactivate the private key and how?  Examples of methods of deactivating private keys include logging out, turning the power off, removing the token/key, automatic deactivation, and time expiration.</li>
        <li>Who can destroy the private key and how?  Examples of methods of destroying private keys include token surrender, token destruction, and overwriting the key.</li>
        <li>Provide the capabilities of the cryptographic module in the following areas: identification of the cryptographic module boundary, input/output, roles and services, finite state machine, physical security, software security, operating system security, algorithm compliance, electromagnetic compatibility, and self tests.  Capability may be expressed through reference to compliance with a standard such as U.S. FIPS 140-1, associated level, and rating.</li>
      </ol>
      <b>BRG</b>  <br>    The CA SHALL implement physical and logical safeguards to prevent unauthorized certificate issuance. Protection of the CA Private Key outside the validated system or device specified above MUST consist of physical security, encryption, or a combination of both, implemented in a manner that prevents disclosure of the Private Key. The CA SHALL encrypt its Private Key with an algorithm and key-length that, according to the state of the art, are capable of withstanding cryptanalytic attacks for the residual life of the encrypted key or key part.<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>  7.5 Cryptographic controls<br> <br> REQ-7.5-01: Appropriate security controls shall be in place for the management of any cryptographic keys and any cryptographic devices throughout their lifecycle.<br> NOTE: See clause 10 of ISO/IEC 27002:2013 [i.3] for guidance.<br>  <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   6.5.2 Private key protection and cryptographic module engineering controls<br> <br> OVR-6.5.2-01: TSP's key pair generation, including keys used by revocation and registration services, shall be carried out within a secure cryptographic device which is a trustworthy system which:
      <ol type="a">
        <li>is assured to EAL 4 or higher in accordance with ISO/IEC 15408 [1], or equivalent national or internationally recognized evaluation criteria for IT security provided this is a security target or protection profile which meets the requirements of the present document, based on a risk analysis and taking into account physical and other non-technical security measures; or </li>
      <li>meets the requirements identified in ISO/IEC 19790 [3] or FIPS PUB 140-2 [12] level 3.</li>
      </ol>
        NOTE 1: Standards specifying common criteria protection profiles for TSP's cryptographic modules, in accordance with ISO/IEC 15408 [1], are currently under development within CEN as CEN TS 419 221-2 [i.16], CEN TS 419 221-3 [i.17], CEN TS 419 221-4 [i.18], or CEN EN 419 221-5 [i.19].<br><br>
      
      OVR -6.5.2-02: The secure cryptographic device shall be operated in its configuration as described in the appropriate certification guidance documentation or in an equivalent configuration which achieves the same security objective.<br> <br> OVR -6.5.2-03: The above secure cryptographic device should be assured as per OVR-6.5.2-01-a), above.  <br> <br> NOTE 2: With the general availability of devices which meet ISO/IEC 15408 [1], it is expected that ISO/IEC 19790 [3] or FIPS 140-2 [12] level 3 will no longer be acceptable.  <br> <br> NOTE 3: This applies also to key generation even if carried out in a separate system.  <br> <br> GEN-6.5.2-04: The CA private signing key shall be held and used within a secure cryptographic device meeting the requirements of OVR-6.5.2-01 and OVR-6.5.2-02 above.<br> <br> GEN-6.5.2-05 [CONDITIONAL]: When outside the secure cryptographic device (see GEN-6.5.2-04 above) the CA private key shall be protected in a way that ensures the same level of protection as provided by the secure cryptographic device.<br> <br> GEN-6.5.2-06: The CA private signing key shall be backed up, stored and recovered only by personnel in trusted roles using, at least, dual control in a physically secured environment (see clause 6.4.2).<br> <br> GEN-6.5.2-07: The number of personnel authorized to carry out the CA private signing key back up, storage and recovery shall be kept to a minimum and be consistent with the CA's practices.<br> <br> GEN-6.5.2-08: Copies of the CA private signing keys shall be subject to the same or greater level of security controls as keys currently in use.<br> <br> GEN-6.5.2-09 [CONDITIONAL]: Where the CA private signing keys and any copies are stored in a dedicated secure cryptographic device, access controls shall be in place to ensure that the keys are not accessible outside this device.<br> <br> OVR -6.5.2-10: The secure cryptographic device shall not be tampered with during shipment.<br> <br> OVR -6.5.2-11: The secure cryptographic device shall not be tampered with while stored.<br> <br> OVR -6.5.2-12: The secure cryptographic device shall be functioning correctly.<br> <br> GEN-6.5.2-13: The CA private signing keys stored on the CA's secure cryptographic device shall be destroyed upon device retirement.<br> <br> NOTE 4: This destruction does not necessarily affect all copies of the private key. Only the physical instance of the key stored in the secure cryptographic device under consideration will be destroyed.<br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.2.1  Cryptographic module standards and controls</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">The Cryptographic Module (HSM) used to operate the Siemens CA is certified to FIPS 140-2 level 3 and the Common Criteria (”CC”), Evaluation Assurance Level (“ EAL”) 4+, which is generally equivalent to Information Technology Security Evaluation Criteria (ITSEC) assurance level E3.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.2.2  Private key (n out of m) multi-person control</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Technical and procedural mechanisms that require the participation of multiple trusted employees to perform sensitive Root CA cryptographic operations are implemented. In order to gain access to the Private Keys, N out of M persons are required. No single person has all the activation data needed for accessing any of the Siemens CA Private Keys.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.2.3  Private key escrow</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">
        Private Key Escrow is not being performed for Root and Issuing CAs. For certifcates related to natural persons or to servers, details are described in the CPS Natural Persons Related Certificates, CPS TLS/SSL resp.
      </td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.2.4  Private key backup</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Siemens Root CA´s Private Key will be backed up and securely stored for the unlikely event of key loss due to unexpected power interruption or hardware failure at separate sites. Key backup will occur as part of CA key generation ceremony. Backed up CA Private Key remains secret and their integrity and authenticity is retained. Private Keys will be re-generated using a key regeneration card set. Key re-generation procedure is documented and must be done under dual control in a physically secure site.<br><br>For Private Keys of Issuing CAs, separate backup hardware cryptographic modules are used and kept secure at separate sites in the trusted operator’s backup locations during operation of the Issuing CA. The following requirements apply to Issuing CA Private Keys.
      <ol>
        <li>Hardware cryptographic modules used for Issuing CA Private Key storage are to meet the requirements of chapter 6.2.1.</li>
        <li>Issuing CA Private Keys are copied to backup hardware cryptographic modules in accordance with chapter 6.2.6.</li>
        <li>Modules containing onsite backup copies and disaster recovery copies of Issuing CA Private Keys are subject to the requirements of chapter 5.1 and chapter 6.2.1.</li>
        <li>Chapter 6.2.3 addresses the backup of Subscriber Private Keys.</li>
    </ol>
      </td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   See Section 5.2.2.<br> <br> 5.2.2 Number of Individuals Required per Task<br> <br> The CA Private Key SHALL be backed up, stored, and recovered only by personnel in trusted roles using, at least, dual control in a physically secured environment.<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.2.5  Private key archival</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Issuing CA Private Key archival: Compare chapter 6.2.4.<br><br>End Entity Subscriber Private Key archival: When Key Pairs reach the end of their Validity Period, the Key Pair will be archived for a period of at least thirty (30) years. This is only applicable for Encryption Certificates.
      </td>
      <td  valign="top"> <b>RFC</b><br> See chapter 6.2<br><br> <b>BRG</b> <br> Parties other than the Subordinate CA SHALL NOT archive the Subordinate CA Private Keys without authorization by the Subordinate CA.<br><br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.2.6  Private key transfer into or from a cryptographic module</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Siemens Root CA´s Key Pairs are generated in the HSM modules in which the keys will be used. <br><br>Private Keys of the Issuing CAs are securely stored exclusively on hardware cryptographic modules.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   If the Issuing CA generated the Private Key on behalf of the Subordinate CA, then the Issuing CA SHALL encrypt the Private Key for transport to the Subordinate CA. If the Issuing CA becomes aware that a Subordinate CA's Private Key has been communicated to an unauthorized person or an organization not affiliated with the Subordinate CA, then the Issuing CA SHALL revoke all certificates that include the Public Key corresponding to the communicated Private Key.<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4> 6.2.7  Private key storage on cryptographic module</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Siemens Root CA´s Private Key is held in HSM backup modules in encrypted form. Where Root CA Key Pairs are backed up to an equivalent hardware cryptographic module, such Key Pairs are transported between modules in encrypted form inside the high security cell of the secure facility.<br><br>Issuing CA Private Keys are stored on hardware cryptographic modules with Common Criteria (CC) Evaluation Assurance Level (EAL) 4+, which is generally equivalent to Information Technology Security Evaluation Criteria (ITSEC) assurance level E3.<br><br>Where Issuing CA Key Pairs are backed up to an equivalent hardware cryptographic module, such Key Pairs are transported between modules in encrypted form inside the high security cell of the secure facility.
      </td>
      <td  valign="top"> <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br> The CA SHALL protect its Private Key in a system or device that has been validated as meeting at least FIPS 140 level 3 or an appropriate Common Criteria Protection Profile or Security Target, EAL 4 (or higher), which includes requirements to protect the Private Key and other assets against known threats.<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.2.8  Method of activating private key</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Siemens Root CA´s Private Key can be activated by introducing the pre-defined number of Operator Cards in the HSM. Root CA Private Key activation requires entry and validation of a PIN/passphrase compliant with specified security parameters.<br><br>Upon issuance, Issuing CA Private Keys are activated on the hardware cryptographic module in the trusted operator high security cell, which is witnessed by a representative of Siemens CA and at least two (2) authorized trusted operator employees and is documented for audit logging purposes.<br><br>End Entity Subscriber Private Keys are generally activated through Subscriber’s use of Activation Data. All Siemens PKI Participants are required to protect the Activation Data for their Private Keys against loss, theft, modification, unauthorized disclosure, or unauthorized use.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.2.9  Method of deactivating private key</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">After use, Siemens Root CA's  Private Keys shall be deactivated by taking the Operator Cards out of the HSM.<br><br>Issuing CA Private Keys on hardware cryptographic modules can be deactivated (and reactivated, if necessary) through deactivation software in the trusted operator’s high security cell, which is witnessed by at least two authorized trusted operator employees and is documented for audit logging purposes.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.2.10 Method of destroying private key</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Siemens Root CA's Private Keys shall be destroyed if they are no longer needed, or when the Certificates to which they correspond expire or are revoked. CA Private Key destruction requires the participation of at least three trusted employees. Private Keys shall be destroyed in a way that prevents their loss, theft, modification, unauthorized disclosure, or unauthorized use. When performed, the destruction process is logged.<br><br>Issuing CA private keys are solely stored within cryptographic hardware modules (see chapter 6.2.7). Their destruction (in case they are no longer needed) requires the participation of three trusted employees. When performed, the destruction process is
logged.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.2.11 Cryptographic Module Rating</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">In general the HSMs are operated with firmware levels that are certified according to FIPS 140-2 Level 3. Siemens reserves the right to operate its HSMs with OEM firmware at levels or configurations that are not certified according to FIPS 140-2 Level 3 if there is an operational or security need for it and if there is no newer FIPS certified firmware or configuration available.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.2<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h3>6.3  Other aspects of key pair management</h3></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>4.6.3.  Other Aspects of Key Pair Management<br> <br> Other aspects of key management need to be considered for the issuing CA, repositories, subject CAs, RAs, subscribers, and other participants.  For each of these types of entities, the following questions potentially need to be answered:
      <ol>
        <li>Is the public key archived?  If so, who is the archival agent and what are the security controls on the archival system?  Also, what software and hardware need to be preserved as part of the archive to permit use of the public key over time?  Note: this subcomponent is not limited to requiring or describing the use of digital signatures with archival data, but rather can address integrity controls other than digital signatures when an archive requires tamper protection.  Digital signatures do not provide tamper protection or protect the integrity of data; they merely verify data integrity.  Moreover, the archival period may be greater than the cryptanalysis period for the public key needed to verify any digital signature applied to archival data.</li>
        <li>What is the operational period of the certificates issued to the subscriber.  What are the usage periods, or active lifetimes, for the subscriber's key pair?</li>
      </ol>
      <b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   6.5.3 Other aspects of key pair management<br> <br> OVR-6.5.3-01: The TSP shall use appropriately the CA private signing keys.<br> In particular:
      <ul>
        <li>OVR-6.5.3-02: The TSP shall not use the CA private signing keys beyond the end of their life cycle.</li>
        <li>GEN-6.5.3-03: CA signing key(s) used for generating certificates as defined in clause 6.3.3, and/or issuing revocation status information, shall not be used for any other purpose.</li>
        <li>GEN-6.5.3-04: The certificate signing keys shall only be used within physically secure premises.</li>
        <li>GEN-6.5.3-05: The use of the CA's private key shall be compatible with the hash algorithm, the signature algorithm and signature key length used for generating certificates, in line with current practice as in requirement GEN-6.5.1-07.</li>
        <li>GEN-6.5.3-06: All copies of the CA private signing keys shall be destroyed at the end of their life cycle.</li>
        <li>GEN-6.5.3-07 [CONDITIONAL]: If a self-signed certificate is issued by the CA, the attributes of the certificate shall be compliant with the defined key usage as defined in Recommendation ITU-T X.509 [6] and aligned with GEN-6.5.3-05.</li>
      </ul>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.3.1  Public key archival</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Siemens CA´s Public Keys are backed up and archived as part of the routine backup procedures.</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.3<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.3.2  Certificate operational periods and key pair usage periods</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">The operational period of a Certificate ends upon its expiration or revocation. The operational period for Key Pairs is the same as the operational period for the associated Certificates, except that they may continue to be used for signature verification The applicability of cryptographic algorithms and parameters is constantly supervised. If an algorithm or the appropriate key length offers no sufficient security during validity period of the Certificate, the concerned Certificate will be revoked and new Certificate Application will be initiated. The maximum operational periods for Root CA Certificates are set forth in table below.


        Certificate                                |              Validity Period
       Siemens Root CA Certificate                 | Up to twelve (12) years

      The Validity Period of the Private Key and Public Key of Issuing CAs, RAs and Subjects ends upon its expiration or revocation. This Validity Period is based on the Validity Period of the Root CA Certificate set forth in the table below.

   INCLUDE TABLE </td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.3<br>  <br><b>BRG</b>  <br>   Subscriber Certificates issued after 1 March 2018 MUST have a Validity Period no greater than 825 days. Subscriber Certificates issued after 1 July 2016 but prior to 1 March 2018 MUST have a Validity Period no greater than 39 months.<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h3>6.4  Activation data</h3></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Activation Data refer to data values required to operate Cryptographic Modules such as a PIN, pass phrase. Activation data protection complies with FIPS 140-1, level 3.<br><br>No Activation Data for Siemens Issuing CA Private Keys are currently provided by its trusted operator to ensure fully automated CA operation with a minimum of manual intervention.<br></td>
      <td  valign="top">  <b>RFC</b>  <br>4.6.4.  Activation Data <br><br>Activation data refers to data values other than whole private keys that are required to operate private keys or cryptographic modules containing private keys, such as a PIN, passphrase, or portions of a private key used in a key-splitting scheme.  Protection of activation data prevents unauthorized use of the private key, and potentially needs to be considered for the issuing CA, subject CAs, RAs, and subscribers.  Such consideration potentially needs to address the entire life-cycle of the activation data from generation through archival and destruction.  For each of the entity types (issuing CA, repository, subject CA, RA, subscriber, and other participants), all of the questions listed in 4.6.1 through 4.6.3 potentially need to be answered with respect to activation data rather than with respect to keys.<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   6.5.4 Activation data<br> <br> GEN-6.5.4-01: The installation and recovery of the CA's key pairs in a secure cryptographic device shall require simultaneous control of at least two trusted employees.<br><br> If the TSP issues a secure cryptographic device:
      <ul>
        <li>SDP-6.5.4-02 [CONDITIONAL]: If the TSP issues a secure cryptographic device, secure cryptographic device (e.g. smartcard) deactivation and reactivation shall be done securely.</li>
        <li>SDP-6.5.4-03 [CONDITIONAL]: If the TSP issues a secure cryptographic device, and where the personalized secure cryptographic device (e.g. smartcard) has associated user activation data (e.g. PIN code), the activation data shall be securely prepared and distributed separately from the secure cryptographic device.</li>
      </ul>
      NOTE: Separation can be achieved by ensuring distribution of activation data and delivery of secure user device at different times, or via a different channel.<br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.4.1  Activation data generation and installation</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top"><b>Further information are documented in the inter CA and HSM management manual.</b></td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.4<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.4.2  Activation data protection</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
     <td  valign="top">><b>Further information are documented in the inter CA and HSM management manual.</b></td>
     <td  valign="top">  <b>RFC</b>  <br>See chapter 6.4<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
     </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.4.3  Other aspects of activation data</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">><b>Further information are documented in the inter CA and HSM management manual.</b></td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.4<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h3>6.5  Computer security controls</h3></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">All computer security technical controls implemented for the Siemens CAs and Certificate Validation Service are established and documented in accordance to the ISMS Regulations.<br><br>All computers at the Siemens CA are subject to constant monitoring. Monitoring results are available 24 hours, 7 days a week. The configuration of system components may only be performed under dual control by operators who have identified with two-factor-authentication using the PKI smart card. Multi-factor authentication is performed by usage of MAG (4-eyes principle by Balabit). <br>
      </td>
      <td  valign="top">  <b>RFC</b>  <br>This subcomponent is used to describe computer security controls such as: use of the trusted computing base concept, discretionary access control, labels, mandatory access controls, object re-use, audit, identification and authentication, trusted path, security testing, and penetration testing.  Product assurance may also be addressed.<br> <br> A computer security rating for computer systems may be required.  The rating could be based, for example, on the Trusted System Evaluation Criteria (TCSEC), Canadian Trusted Products Evaluation Criteria, European Information Technology Security Evaluation Criteria (ITSEC), or the Common Criteria for Information Technology Security Evaluation, ISO/IEC 15408:1999.  This subcomponent can also address requirements for product evaluation analysis, testing, profiling, product certification, and/or product accreditation related activity undertaken.<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   6.5.5 Computer security controls<br> <br> OVR-6.5.5-01: The requirements REQ-7.4-01, REQ-7.4-02, REQ-7.4-03 and REQ-7.4-10 in ETSI EN 319 401 [8] shall apply.<br> <br> NOTE: Requirements for the trustworthy systems can be ensured using, for example, systems conforming to CEN TS 419 261 [i.9] or to a suitable protection profile (or profiles), defined in accordance with<br>ISO/IEC 15408 [1].<br> <br> In addition the following particular requirements apply:<br> <br> GEN-6.5.5-02: Local network components (e.g. routers) shall be kept in a physically and logically secure environment.<br> <br> GEN-6.5.5-03: Local network components (e.g. routers) configurations shall be periodically checked for compliance with the requirements specified by the TSP.<br> <br> GEN-6.5.5-04: The TSP shall enforce multi-factor authentication for all accounts capable of directly causing certificate issuance.<br> <br> DIS-6.5.5-05: Dissemination application shall enforce access control on attempts to add or delete certificates and modify other associated information.<br> <br> CSS-6.5.5-06: Revocation status application shall enforce access control on attempts to modify revocation status information.<br> <br> OVR-6.5.5-07: Continuous monitoring and alarm facilities shall be provided to enable the TSP to detect, register and react in a timely manner upon any unauthorized and/or irregular attempts to access its resources.<br><br>EXAMPLE: This can use an intrusion detection system, access control monitoring and alarm facilities.<br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.5.1  Specific computer security technical requirements</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">See chapter 6.5</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.5<br>  <br><b>BRG</b>  <br>   The CA SHALL enforce multi-factor authentication for all accounts capable of directly causing certificate issuance.<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.5.2  Computer security rating</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.5<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h3>6.6  Life cycle technical controls</h3></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>This subcomponent addresses system development controls and security management controls.<br> <br> System development controls include development environment security, development personnel security, configuration management security during product maintenance, software engineering practices, software development methodology, modularity, layering, use of failsafe design and implementation techniques (e.g., defensive programming) and development facility security.<br> <br> Security management controls include execution of tools and procedures to ensure that the operational systems and networks adhere to configured security.  These tools and procedures include checking the integrity of the security software, firmware, and hardware to ensure their correct operation.<br> <br> This subcomponent can also address life-cycle security ratings based, for example, on the Trusted Software Development Methodology (TSDM) level IV and V, independent life-cycle security controls audit, and the Software Engineering Institute's Capability Maturity Model (SEI- CMM).<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   6.5.6 Life cycle security controls<br> <br> OVR-6.5.6-01: The requirements identified in ETSI EN 319 401 [8], clause 7.7 shall apply for all service components. In addition the following particular requirements apply:<br> <br> OVR-6.5.6-02 [NCP]: Capacity demands shall be monitored and projections of future capacity requirements shall be made to ensure that adequate processing power and storage are available.<br> <br> OVR-6.5.6-03 [PTC]: Clause 5 of the BRG [5] shall apply.<br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.6.1  System development controls</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.6<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h4>6.6.2  Security management controls</h4></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.6<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
     <td  valign="top"><h4>6.6.3  Life cycle security controls</h4></td>
     <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>See chapter 6.6<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h3>6.7  Network security controls</td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>4.6.7.  Network Security Controls<br> <br> This subcomponent addresses network security related controls, including firewalls.<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   6.5.7 Network security controls<br> <br> OVR-6.5.7-01: The requirements identified in ETSI EN 319 401 [8], clause 7.8 shall apply. In addition the following particular requirements apply:<br> <br> OVR-6.5.7-02 The TSP shall maintain and protect all CA systems in at least a secure zone and shall implement and configure a security procedure that protects systems and communications between systems inside secure zones and high security zones.<br> <br> OVR-6.5.7-03: The TSP shall configure all CA systems by removing or disabling all accounts, applications, services, protocols, and ports that are not used in the CA's operations.<br> <br> OVR-6.5.7-04: The TSP shall grant access to secure zones and high security zones to only trusted roles.<br> <br> OVR-6.5.7-05: The Root CA system shall be in a high security zone.<br>
      </td>
    </tr>
    <tr>
      <td  valign="top"><h3>6.8  Time-stamping</h3></td>
      <td  valign="top"></td>
    </tr>
    <tr>
      <td  valign="top">Empty</td>
      <td  valign="top">  <b>RFC</b>  <br>This subcomponent addresses requirements or practices relating to the use of timestamps on various data.  It may also discuss whether or not the time-stamping application must use a trusted time source.<br>  <br><b>BRG</b>  <br>   Empty<br>  <br><b>ETSI EN 319 401 V2.2.1</b> <br>    <br><b>ETSI EN 319 411-1 V1.2.1</b><br>   6.5.8 Timestamping<br> <br> NOTE: Not in the scope of the present document. See ETSI EN 319 421 [i.15] for policy requirements for TSPs issuing time-stamps.<br>
      </td>
    </tr>
</table>
